- describe how to batch updates with the `HTMLCanvasElement`
  - see `DrawingCanvas` renderer in Hugo Systems - setting a background,
    updating dimensions, clearing the canvas, and drawing on the canvas can't
    all be done with multiple functions that call `cancelAnimationFrame` - all
    updates that result in the canvas having to be re-rendererd need to be
    added to a queue, and then drawn in a single `requestAnimationFrame` call