# virtual-canvas.inc

This small library provides a `VirtualCanvas` structure which represents a rectangle and a resolution. The canvas can be used to create a virtual space where coordinates can be scaled within that space.

This was originally written for bitmap scaling so a bitmap of size 1000x1000 pixels could be used to represent the entire San Andreas map and pixel coordinates could be mapped to world coordinates. This was needed because the game's world occupies a space that runs from `-3000.0` X and `-3000.0` Y to `3000.0` X and `3000.0` Y.

## Installation

Simply install to your project:

```bash
sampctl package install Southclaws/samp-virtual-canvas
```

Include in your code and begin using the library:

```pawn
#include <virtual-canvas>
```

## Usage

Create a virtual canvas variable:

```pawn
new canvas[VirtualCanvas];
```

Either fill it manually or use the helper function:

```pawn
CreateVirtualCanvas(-3000.0, 3000.0, -3000.0, 3000.0, 1000, 1000, canvas);
```

This creates a canvas for the entire San Andreas map with a resolution 6 times smaller than the map at 1 metre scale.

Now you can retrieve coordinates from within the `0..1000` space and they are scaled up to the `-3000..3000` space.

```pawn
GetVirtualCanvasPos(canvas, 500, 500, x, y); // This stores the coordinates 0.0, 0.0 into x and y.
GetVirtualCanvasPos(canvas, 250, 250, x, y); // This stores the coordinates -1500.0, -1500.0 into x and y.
GetVirtualCanvasPos(canvas, 750, 750, x, y); // This stores the coordinates 1500.0, 1500.0 into x and y.
```

## Testing

To test, simply run the package:

```bash
sampctl package run
```

And observe the output. Play with the values in `test.pwn`.
