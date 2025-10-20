
# Integrating Your Module into the Core Generator

Once you have a working, standalone structure module, the final step is to add it to the main `settlement/core.py` file. This will make it available to the main settlement generator and add your structure to the set of buildings generated in our village.

### 1. Open `settlement/core.py`
This file orchestrates the entire settlement generation. It contains a list named `BUILDING_TYPES` which registers all available structures.

### 2. Add an Import Statement
At the top of the file, in the section marked for building imports, add a line to import your new module. Let's assume you've created `MakeForge.py`.

```python
# ... other imports
# ===== BUILDING IMPORTS =====
import MakeTower
import MakeHouse
import MakeForge  # <--- ADD THIS LINE
# ============================
# ... rest of the file
```

### 3. Register Your Structure in BUILDING_TYPES
Find the BUILDING_TYPES list near the top of the file and add a new StructureType entry for your structure.

```python
BUILDING_TYPES = [
    # ... other structures
    StructureType(module=MakeTower, function_name="tower", weight=1, height_modifier=15),
    StructureType(module=MakeForge, function_name="forge", weight=3), # <--- ADD THIS LINE
]
```
`StructureType` Parameters Explained:
- `module`: The name of the module you just imported (e.g., MakeForge).
- `function_name`: A string containing the name of your main rule function defined in the module's entrypoint (e.g., "forge").
- `weight`: An integer that determines how frequently your structure appears. A higher weight means it's more common.
- `height_modifier` (Optional): An integer to adjust the vertical placement. Useful for multi-level buildings like towers (the default height is more suitable for single story structures). If you notice your buildings getting squished or cut off - this is the parameter to adjust!

### 4. Test the Integration
1. Save your changes to core.py.
2. Go into Amulet and Refresh the operations list.
3. Run the main Settlement Generator operation.
4. Your forge should now appear as one of the buildings in the generated settlements! It will also be a toggleable option in the menu that appears when you run the generator.

**Next Steps:** Great work! Feel free to check out the Assignments page to dig deeper into structure generation: **[Assignments](./ASSIGNMENTS.md)** (WIP).