Parent: [[+ bash]]

```bash
until foo_process_is_exiting_true; do
	echo "foo is not yet ready" && sleep 1
done

echo "foo is ready!"

do_thing_waiting_for_foo
```

- `until` will loop until the command it is evaluating returns a zero exit code
