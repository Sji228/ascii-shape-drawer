# ASCII Shape Drawer

A small C++ program that draws circles, rectangles and squares onto an ASCII canvas, based on a plain-text config file. Written as a university assignment (Programming, 2024) to practise classes, inheritance and polymorphism.

```
|====================|
|....................|
|...............****.|
|..@@@@@...#....****.|
|..@@@@@.#####..****.|
|..@@@@@.#####..****.|
|.......#######......|
|........#####.......|
|........#####.......|
|..........#.........|
|....................|
|====================|
```

## Build and run

```bash
g++ -o draw draw.cpp
./draw config.txt
```

The result is written to the output file named in the config.

## Config format

```
20 10            # canvas width and height
output.txt       # output file
.                # background symbol
Circle 10 5 3 #
Rectangle 2 2 5 3 @
Square 15 1 4 *
```

| Shape | Line format |
|---|---|
| Circle | `Circle x y radius symbol` (x, y = centre) |
| Rectangle | `Rectangle x y width height symbol` (x, y = top-left corner) |
| Square | `Square x y side symbol` (x, y = top-left corner) |

Shapes are drawn in order, so later ones cover earlier ones. Anything outside the canvas is clipped. The config file itself must not contain comments.

## Design

- `Canvas` is an abstract interface; `ASCIICanvas` stores the pixel grid and renders it with a border.
- `Figure` is the abstract base for shapes; `Circle` and `Rectangle` implement `draw()`, and `Square` reuses `Rectangle`.
