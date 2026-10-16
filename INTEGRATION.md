# Settlement Generator Integration

Once you have a standalone structure module, the final step is to add it to the main settlement generator. This will register your structure with the settlement generator so it can appear as a building in the generated villages.

## 1. Open `generator\features\palette.py`

The `generator\features\palette.py` script orchestrates village layouts, road paths, lot zoning, and structure placement. It maintains a registry of available buildings called `BUILDING_TYPES`.

---

## 2. Add an Import Statement

At the top of the `generator\features\palette.py` file, notice the try blocks where structures are imported. Add an import statement for your newly created module. Let's assume you've created `MakeForge.py`:

```python
try:
    import MakeForge
except Exception: 
    MakeForge = None
```

---

## 3. Register your structure in `BUILDING_TYPES`

Locate the `BUILDING_TYPES` list in `generator\features\palette.py`. Add a new `BuildingType` entry for your building:

```python
if MakeForge is not None:
    BUILDING_TYPES.append(
        BuildingType(
            name="forge",
            module=MakeForge,
            function_name="forge",
            weight=5,
            roles=("materials"),
            min_height=5,
            max_height=10,
            min_footprint=(10, 10),
            max_footprint=(20, 20),
            placement="one_per_site_far",
        )
    )
```

---

### `BuildingType` parameters explained:

- `module`: The name of the module you just imported (e.g., MakeForge).
- `function_name`: A string containing the name of your main rule function defined in the module's entrypoint (e.g., "forge").
- `weight`: An integer that determines how frequently your structure appears. A higher weight means it's more common.
- `roles`: Depending on the roles of the structure, it will be placed in a diferent location.
- `height`: The minimum or maximum height the structure will generate to.
- `footprint`: The minimum or maximum space the structure will take up.
- `placement`: Depending on placement, the structure will either generate in a village or on the outskirts,

## 4. Test the Integration
1. Save your changes.
2. Go into Amulet and Refresh the operations list. If this does not work, restart Amulet.
3. Run the main settlement generator operation with necessary parameters.
4. Your forge should now appear as one of the buildings in the generated settlements! 
5. If you are interested in working on the generator, contact Michael for help.

**Next Steps:** Now that you know how to integrate your structures into the settlement generator, learn how to create more elaborate textures and color palettes in the **[Gradients](./GRADIENTS.md)** guide.