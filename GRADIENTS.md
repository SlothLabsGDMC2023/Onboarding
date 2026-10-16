# Gradients

Gradients are an exciting new addition to SlothLab, developed by Ethan Duong. This feature gives team members a new way to texture builds using customizable parameters. To view the slideshow that this guide is based off of visit **[Quick Start Guide: Gradient Fill]**(https://docs.google.com/presentation/d/1KVW5M-FEO16wP0szwOBbdVXi9Sf-WXtfIejLT--LkOY/edit?usp=sharing).

## 1. Update your grammar files

To prevent merge conflicts or accidentally modifying Ethan's branch, do not work directly on his branch. Instead, pull the single updated grammar file into your branch.

1. Make sure you are on your own feature branch: `git status`
2. Checkout only the `MCSplitGrammar.py` file from Ethan's branch into your branch:
```bash
git checkout origin/ethan/houses/gradients -- MCSplitGrammar.py
```
3. Copy this updated `MCSplitGrammar.py` file into your Amulet `plugins/operations` directory so Amulet can load the new `Gradient` class.

## 2. Import Gradient in your structure file

In the structure module you wish to add gradients to, add `Gradient` to your grammar import statement:

```python
from amulet.api.block import Block
from MCSplitGrammar import rule, split, fill, void, Dimension, clearrules, Gradient

clearrules(__file__)
```

## 3. Define your Gradient

Initialize your gradient by passing the block types in order from the low end to the high end of the chosen axis. For example, when using the Y-axis, pass blocks from bottom to top.

```python
mossy_wall = Gradient(
    "mossy_cobblestone",
    "cobblestone",
    "stone_bricks",
    method="linear",
    direction="y"
)
```

### `Gradient` parameters explained:

- `direction`: Sets the axis along which the blend occurs ("x", "y", or "z"). If nothing is selected, it will default to "y".
- `method`: Defines the blending algorithm ("normal", "linear", or "bezier"):
  * "normal": Divides the box into solid stripes without any mixing.
  * "linear": Creates solid bands of each material, separated by transition zones where one material fades into the next.
  * "bezier": This is the default setting. Smoothly blends materials without any solid bands in the middle. Only the first and last materials are 100% pure, and only at the ends. 

## 4. Apply the `Gradient` using `fill()`

Use your gradient object inside your `@rule` functions anywhere you would normally pass a block to `fill()`:

```python
@rule
def walls():
    # Split horizontally to create exterior walls
    with split(Dimension.X, [1, -1, 1]):
        fill(mossy_wall)  # Left wall
        with split(Dimension.Z, [1, -1, 1]):
            fill(mossy_wall)  # Front wall
            void()            # Hollow interior
            fill(mossy_wall)  # Back wall
        fill(mossy_wall)  # Right wall
```

You can also pass `Gradient` directly into `fill()`:

```python
fill(Gradient("calcite", "diorite", "andesite", method="bezier", direction="y"))
```

## 5. Test in Amulet
1. Save your changes.
2. Go into Amulet and click Refresh the Operations menu
3. Follow the steps in the **[Amulet Crash Course](./AMULET-CRASH-COURSE.md)** guide to generate your structure.
4. If you are interested in learning about the math behind gradients, check out Ethan's documentation in the `ethan/houses/gradients` branch by viewing the `GRADIENT_README.md` file.