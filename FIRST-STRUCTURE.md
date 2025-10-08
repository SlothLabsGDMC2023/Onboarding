# Your First Structure

Here you will learn how to create a new, standalone, structure module.

> **Very Important!**
>
> Before beginning, ensure you have copied the contents from the _Master branch_ from the SlothLab repository into Amulet's `plugins\operations` folde. This ensures Amulet has access to the Box-Split Grammar, Settlement Generation, and other required systems. If you skip this step, your operation will not run correctly and you will be missing files. In short:
>
>* The contents of Amulet\plugins\operations should match the contents of the SlothLab Master branch.
>* When you create your own structure generation module, do so within the plugins\operations folder so you can test and run it locally.
>* If there are major updates to the Grammar or Settlement Generation code, you can safely pull from the SlothLab repo again and copy only the updated files into Amulet’s plugins\operations folder.

### 1. Plan Your Structure

First, decide what you want to build! We suggest you start by thinking of a fitting building our medieval village could use (check the current integrated structures in the `core.py` file).

* **Find a Reference:** We welcome you to build your own structure first in-game to explore the necessary architectural requirements, or find a reference online. A great source of in-game buildings to model your structure off of is [Build It](https://builditapp.com/).

* **Think in Grammar:** Once you have a design, think about how it would have to work logically with our grammar in mind. How would you divide it into individual rows and columns? Try to imagine how you might roughly need to go about it—the types of splits, what sort of variation you would want, the block types, etc.

 > **Important:** You will soon notice that complex structure designs tend to be relatively difficult to replicate with the grammar, so consider simplifying the intricacies of the structure you choose for now to better get a hang of the system. 

### 2. Create Your Module File
Navigate to the `plugins/operations` folder.
1.  **Create** a new Python file, e.g., `MakeForge.py`.
2.  **Add Boilerplate Code:** At the top of your file, add the necessary imports.

    ```python
    # Amulet-specific imports
    from amulet.api.selection import SelectionGroup
    from GrammarBox import BoundingBox

    # Grammar-specific imports
    from MCSplitGrammar import rule, split, void, fill, start_symbol, Dimension, clearrules

    # This clears any previously loaded rules from this file, ensuring a clean slate on refresh
    clearrules(__file__)
    ```

### 3. Write Your Grammar Rules
This is where you define the structure's logic. Start with a top-level rule.

```python
@rule
def forge():
    # This example builds a simple 5x5x5 stone shell with a hollow center
    with split(Dimension.Y, [1, -1, 1]): # Split vertically (bottom, middle, top)
        fill("minecraft:stone_bricks")   # Fill the bottom layer

        # In the middle layer, we build the walls
        with split(Dimension.X, [1, -1, 1]):
            fill("minecraft:stone_bricks")   # Left wall
            with split(Dimension.Z, [1, -1, 1]):
                fill("minecraft:stone_bricks")   # Front wall
                void()                           # Hollow interior
                fill("minecraft:stone_bricks")   # Back wall
            fill("minecraft:stone_bricks")   # Right wall

        fill("minecraft:stone_bricks")   # Fill the top layer
```
### 4. Add the Amulet Entrypoint
Amulet needs a specific function and dictionary to run your script. Add this to the bottom of your file. It initializes the grammar on Amulet's selection box and calls your starting rule.
```python
def performOperation(world, dim, selection_group, options):
    box = selection_group.selection_boxes[0]
    # Initialize the grammar system
    sc = start_symbol(BoundingBox(box.min, box.shape), world, dim)
    if sc is not None:
        forge() # This calls your main rule!

# This dictionary tells Amulet the name to display in the operations list
export = {
    "name": "Make Forge", # This name will appear in the Amulet UI
    "operation": performOperation,
}
```
### 5. Test Your Module

1. Save your MakeForge.py file.
2. Go to Amulet, make a box selection, and click Refresh in the Operation menu.
3. Your operation, "Make Forge", should now appear in the dropdown.
4. Select it and click Run Operation. Your forge should appear in the world!


## Example: Creating a `MakeTower` Module
   ```python
   from MCSplitGrammar import rule, split, void, fill, start_symbol, Dimension
   from GrammarBox import BoundingBox
   from amulet.api.selection import SelectionGroup, SelectionBox
   clearrules(__file__)
   weight = 1

   @rule
   def tower():
       # ... split and fill blocks ...

   def performOperation(world, dim, sel, opt):
       box = sel.selection_boxes[0]
       sc = start_symbol(BoundingBox(box.min, box.shape), world, dim)
       if sc:
           tower()

   export = {
      "name": "Make Tower", 
      "operation": performOperation
   }
   ```
**Next Steps:** Now that you're comfortable setting up your own structure module in Amulet, learn how to integrate your structure into our Settlement Generator with this guide: **[Integrating Your Module into the Core Generator](./INTEGRATION.md)**.