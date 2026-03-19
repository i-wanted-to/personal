# gvg

GPU Vector Graphics generated from traditional vector graphics.

Traditional vector graphics (e.g. SVGs) store a sequence of shapes in back to front order, and each
shape stores a sequence of curves in the order they connect. This order is useful for a sequential
renderer that populates the entire scene on a random-access target. In this case, each curve can be
evaluated in order, and the corresponding portion of the target can be updated.

In parallel rendering (e.g. on a GPU), the renderer (fragment shader) runs for a single pixel.
Following a traditional rendering approach would result in every pixel evaluating every curve to
determine what effect each curve had on the pixel. Although this would work, it would be
unreasonably slow.

The GPU Vector Graphics format reorganizes the vector data according to its spatial area of
influence. This allows each parallel renderer (fragment shader) to query just the data relevant to
the renderer's output location, rather than looping through every shape/curve in the entire image.
