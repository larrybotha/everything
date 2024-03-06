- describe how to batch updates with the `HTMLCanvasElement`
  - see `DrawingCanvas` renderer in Hugo Systems - setting a background,
    updating dimensions, clearing the canvas, and drawing on the canvas can't
    all be done with multiple functions that call `cancelAnimationFrame` - all
    updates that result in the canvas having to be re-rendererd need to be
    added to a queue, and then drawn in a single `requestAnimationFrame` call
- describe event delegation where one listens on the `capture` propagataion mode
  in the DOM to handle changes to child events, such as the `load` event of
  dynamically changing images from a parent
  - see the `Canvas` component in `DrawingCanvas` in Hugo Systems - we need to
    know when images are loaded so that we can change the background, but we
    don't want any convoluted passing down of function props etc. - ideally
    we want the `Canvas` component to have some way to listen for when images
    change. The `load` event is such an event, but it does not bubble... so...
    we can indicate on a parent element to listen by specifying that it should
    be attached to the `capture` propagation mode of the event
- do a series of videos building the `DrawingCanvas` from Hugo Systems
  - demonstrate using native DOM APIs to observe:
    - mutations
    - resizing
    - captured load events
    - request animation frame for rendering
  - show the power of state machines
  - show how pleasant Svelte is to work with
- investigate [SurrealDB](https://docs.surrealdb.com/docs/integration/sdks/rust/)
  for interacting programmatically with databases using Rust
- demonstrate how to derive `map` from `for` in Python and JavaScript
- build a Chrome extension that enables `hx-boost="true"` on the site you're
  currently visiting
- building accessible components in javascript using the
  [ARIA Authoring Practices Guide (APG)](https://www.w3.org/WAI/ARIA/apg/patterns/)
  - build them first in vanilla JS, and then in htmx
