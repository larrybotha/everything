---
tags:
  - resource/video
---

Link: https://www.youtube.com/watch?v=f9IrbW13C_c

- to make processes run in parallel, use goroutines, i.e.:

    ```go
    // https://go.dev/play/p/9l6majvBgq_o
    package main

    import (
        "fmt"
        "time"
    )

    func main() {
        tasks := []string{"a", "b", "c"}

        for _, x := range tasks {
            go process(x)
        }
    }

    func process(x string) {
        fmt.Println("started ", x)

        time.Sleep(time.Second)

        fmt.Println("finished ", x)
    }
    ```

    This will run successfully, without output, because we're not waiting
    for any of the goroutines to complete

- to wait for goroutines, one can use a `WaitGroup`:

    ```go
    // https://go.dev/play/p/_LIybb-rBmt
    package main

    import (
        "fmt"
        "time"
        "sync"
    )

    func main() {
        tasks := []string{"a", "b", "c"}
        // 1
        var wg sync.WaitGroup

        // 2
        wg.Add(len(tasks))

        for _, x := range tasks {
            go func() {
                process(x)
                // 3
                wg.Done()
            }()
        }

        // 4
        wg.Wait()
    }

    func process(x string) {
        fmt.Println("started ", x)

        time.Sleep(time.Second)

        fmt.Println("finished ", x)
    }
    ```

    We do the following:

    1. init a `WaitGroup`
    2. increment the counter of the `WaitGroup` so that it knows how many times
        it should wait. It releases goroutines when it hits 0
    3. decrement the counter using `WaitGroup.Done` each time a call completes
    4. wait for the counter to hit 0
- `WaitGroup` allows for waiting for tasks to finish, but it doesn't allow us
    to do anything with the result of the task

    To process the result of a task, we need to send those results to a channel:

    ```go
    // https://go.dev/play/p/ExIbKGvs6rY
    package main

    import (
        "fmt"
        "time"
    )

    func main() {
        tasks := []string{"a", "b", "c"}
        // 1
        resultChannel := make(chan string)
        // 2
        defer close(resultChannel)

        for _, x := range tasks {
            go func() {
                // 3
                process(x, resultChannel)
            }()
        }

        // 4
        for range len(tasks) {
            // 5
            result := <-resultChannel
            fmt.Println(result)
        }

        fmt.Println("done")
    }

    func process(x string, ch chan<- string) {
        fmt.Println("started ", x)

        time.Sleep(time.Second)

        // 6
        ch <- fmt.Sprint("finished ", x)
    }
    ```

    This is what we're doing:

    1. create a channel that will receive strings
    2. ensure we close the channel when the function exits
    3. pass the channel to the caller so that it can send strings to the channel
    4. loop over the range of tasks
    5. get the result out of the channel each time a task completes -
        execution of the code blocks until there is a value to be read. Values are
        removed from a channel as they are read
    6. send the result of the caller to the channel. This is another place where
        execution will be blocked - a new value will only be added to the channel
        when the channel is empty

    Channels can be send (`chan<- T`), receive (`<-chan T`), or bi-direction (`chan T`)

    We `send` to a channel by placing the channel on the left of the arrow:

    ```
    ch <- 3 // send 3 to the channel
    ```

    We `receive` from a channel by placing the arrow on the right of the arrow:

    ```
    x := <-ch // receive a value out of the channel
    ```

    Always specify directionality of a channel - potentially dangerous not to

    The above demo is an example of an unbuffered channel - a channel that allows
    only a single value to be written to a channel at a time
- We can use a buffered channel along with a `WaitGroup` to ensure we're not blocking
    on every iteration of the task being sent to the channel:

    ```go
    // https://go.dev/play/p/0NgokWdNU1d
    package main

    import (
        "fmt"
        "time"
        "sync"
    )

    func main() {
        tasks := []string{"a", "b", "c"}
        // 1
        var wg sync.WaitGroup
        // 2
        resultChannel := make(chan string, len(tasks))

        // 3
        wg.Add(len(tasks))

        for _, x := range tasks {
            go func() {
                // 4
                defer wg.Done()
                process(x, resultChannel)
            }()
        }

        // 5
        go func() {
            // 6
            wg.Wait()

            // 7
            defer close(resultChannel)
        }()

        // 8
        for result := range resultChannel {
            fmt.Println(result)
        }

        fmt.Println("done")
    }

    func process(x string, resultChannel chan<- string) {
        fmt.Println("started ", x)

        time.Sleep(time.Second)

        // 9
        resultChannel <- fmt.Sprint("started ", x)
    }
    ```

    With this approach, we now have the following:

    1. we initialise a `WaitGroup` so that we can defer blocking of the channel
        until all of the tasks have completed
    2. we specify the size of the channel - the number of items it'll hold before
        it begins locking reads / writes
    3. we increment the counter of the `WaitGroup`
    4. we use `wg.Done()` to decrement the `WaitGroup` when the task completes
    5. a goroutine is then executed to allow the `WaitGroup` to do its job without
        blocking
    6. we wait for the `WaitGroup`s counter to hit 0
    7. then close the channel - closing the channel allows us to `range` over it
        a finite number of times
    8. the code moves directly from #5 to here, iterating over each value as it
        becomes available to the channel. We can iterate directly because we closed
        the channel at #7 - if we hadn't then the channel would continue iterating
        beyond the initialised size, and panic

    The execution looks more like the following:

    `1 -> 2 -> 3 -> 5 -> 6 -> 4 -> 9 [a,b,c] -> 8 [a,b,c] -> 7`
- we can introduce control flow to goroutines and channels using `select`. e.g.
    if we want to handle timeouts / long-running requests:

    ```go
    // https://go.dev/play/p/8kqSg6RfWY7
    package main

    import (
        "fmt"
        "time"
    )

    func main() {
        tasks := []string{"a", "b", "c"}
        // 1
        resultChannel := make(chan string, len(tasks))
        // 2
        defer close(resultChannel)

        for i, x := range tasks {
            go func() {
                // 3
                process(x, resultChannel, i + 1)
            }()
        }

        // 4
        for range len(tasks) {
            result := <-resultChannel
            fmt.Println(result)
        }
    }

    func process(x string, result chan<- string, taskDuration int) {
        fmt.Println("started ", x)

        // 5
        taskDone := time.After(time.Duration(taskDuration) * time.Second )
        // 6
        timeout := time.After(time.Duration(2.5 * float32(time.Second)))

        // 7
        select {
            // 8
            case <-timeout:
                result <- fmt.Sprint("timed out ", x)
            // 9
            case <-taskDone:
                result <- fmt.Sprint("finished ", x)
        }
    }
    ```

    What we're doing here is:

    1. creating a buffered channel, allowing N tasks before it will lock
    2. ensuring we close the channel when the function exits
    3. passing in a faux duration for each task
    4. for the number of tasks we've defined in the channel, consume each
        result, blocking until we get each result
    5. we create the faux duration of the task using `time.After`, which
        returns a sending channel, which sends after the duration is met
    6. we create a timeout using `time.After`. Another channel, which will
        send a result when the duration is met
    7. `select` is like `switch` but for channels
    8. if the timeout channel sends first, send `timed out` to our result
        channel
    9. otherwise, if the task completes before timing out, send that to the
        channel

    The problem with this approach is that our process needs to know of the
    timeout internally. Instead, we can use `context` to externally define
    the timeout, and make it available to the task
- a timeout context can be created, allowing us to specify a timeout channel
    outside of our tasks:

    ```go
    // https://go.dev/play/p/IUJo68imfdD
    package main

    import (
        "fmt"
        "time"
        "context"
    )

    func main() {
        tasks := []string{"a", "b", "c"}
        resultChannel := make(chan string, len(tasks))
        // 1
        timeout = time.Duration(2.5 * float32(time.Second))

        // 2
        ctx, cancel := context.WithTimeout(context.Background(), timeout)
        // 3
        defer cancel()

        for i, task := range tasks {
            go func() {
                // 4
                process(ctx, task, resultChannel, i + 1)
            }()
        }

        for range len(tasks) {
            result := <-resultChannel
            fmt.Println(result)
        }

        fmt.Println("done")
    }

    func process(ctx context.Context, x string, result chan<- string, taskDuration int) {
        fmt.Println("started", x)

        taskDone := time.After(time.Duration(taskDuration) * time.Second)

        select {
            // 5
            case <-ctx.Done():
                result <- fmt.Sprint("timed out", x)
            case <-taskDone:
                result <- fmt.Sprint("finished", x)
        }
    }
    ```

    With this approach the timeout can be passed via context. We're doing
    the following:

    1. creating a timeout outside of the task
    2. creating a context that has a timeout
    3. ensure that work on the context is stopped when the function exits
    4. pass the context into the task
    5. use `select` to evaluate whether the task completed, or if the timeout
        in the context was exceeded using the `Done()` method which returns a
        channel
- the combination of goroutines, channels, and `select` form one of two ways to
    write concurrent code in Go
- for working with shared data across multiple goroutines, mutexes offer a
    more succinct alternative

## links and resources

- [ranging over channels](https://golangr.com/range-channel)




















