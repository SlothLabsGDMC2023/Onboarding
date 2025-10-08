# Amulet Editor Crash Course

Learn how to set up your environment and familiarize yourself with the basics of the Minecraft world editor, Amulet. 

 > **Important:** If you do not already have Git installed or the SlothLab repo set up, click [here](./REPO-SETUP.md)!

## 1. Software Installation 
You will need both **Minecraft** and **Amulet**.

* **Minecraft:** A copy of [Minecraft](https://www.minecraft.net/en-us) is needed to create and view worlds to edit in Amulet. 

* **Amulet:** Visit the [Amulet](https://www.amuletmc.com/) website and follow the provided instructions to download the software for your specific OS. Extract the ZIP and locate the `/Amulet` folder. Find `amulet_app.exe`.  

> **Important:** We suggest creating a shortcut for Amulet (if not created by default) for ease of access. 

## 2. Prepare Your Minecraft World

Before you can edit a world in Amulet, you have to first generate the terrain in Minecraft.

> **Important:** Chunks must be loaded in Minecraft itself before you can access them in Amulet. Make sure you have opened the world you'll be testing with in the actual Minecraft game first to load in the chunks.

You can find your Minecraft save files here:

* **Windows:** Type `%appdata%` in the Start Menu or File Explorer address bar and navigate to the `.minecraft/saves` folder. 
* **macOS:** In Finder, press `Cmd+Shift+G`, then enter: `~/Library/Application Support/minecraft/saves` to find your Minecraft world saves.

This is where you can see your existing Minecraft worlds or drag in new ones (like the Generation Competition maps). Of course, this would be empty if you haven't ever loaded into a world in Minecraft yet. 

Make sure to open your worlds from this folder in the Amulet editor.

If you don't have Minecraft, do not want to generate a map, or just want to see what the competition map looked like in 2025, you can download it from [here](https://www.dropbox.com/scl/fi/jsb1u4pjrs585sdj3e3kx/GDMC-2025-submission-map.zip?rlkey=2ckuzun7t3oyzvtskkxf354h4&e=1&st=mqeo01d4&dl=0). In the 2025 competition, the four locations where settlements had to be generated were the Riverlands at (0, 0), +-500; the Mesa Valley at (4000, 0), +-200; the Caldera at (9000, 500), +- 200; and the Pirate Coast at (-2850, 4800), +- 350; (all given as (x,z) with the range within the settlement had to be built).

## 3. Using Amulet

Now try launching the Amulet application `amulet_app.exe` and load into your Minecraft World. 

#### Basic Controls
* **Look Around:** Right-click and move your mouse.
* **Move:** Use `W`, `A`, `S`, `D`.
* **Ascend/Descend:** Use `Space` to go up and `Shift` to go down.
* **Change Speed:** Scroll your mouse wheel up or down to increase or decrease your movement speed.

#### Top-Right UI
* **`3D/2D`:** Switches the view from a 3D perspective to a top-down 2D map.
* **`(X,Y,Z Coords)`:** Shows your current coordinates. You can click this to manually edit them and teleport.
* **`b/s`:** Displays your current movement speed in blocks per second.
* **`Dimension`:** Lets you switch Minecraft dimensions (e.g., Nether, The End). We don't really use this.
* **`Undo/Redo Buttons`:** Use these to undo or redo generations. This also saves the positions of your previous selection boxes, which is very useful.
* **`Save Changes`:** Tracks unsaved changes. The `Ctrl+S` hotkey is useful here.
* **`Close World`:** Closes the current world.

## 4. Running Operations in Amulet

in Amulet, **Operations** are the python scripts we use to manipulate the Minecraft world. With the Box-Split Grammar, we can easily leverage this functionality to write building generation algorithms! 

#### How to Run an Operation
1.  **Make a Selection:** Click the **`Select`** button in the bottom UI and drag a selection box in the world. You can drag and resize each face of the selection box by clicking and dragging it.
2.  **Open the Operation Menu:** Click the **`Operation`** button in the bottom UI. A new menu will appear on the top left.
3.  **Use the Operation Menu:**
    * **Dropdown Menu:** This is where you select which operation to run.
    * **Refresh Button:** Reloads the operations from the plugins folder. **You will use this a lot** as you edit your structure generator file and want to see your changes.
    * **Folder Icon:** This opens the folder where all the python scripts are located. This is the folder you will be working in with your code editor. The path will be something like `AppData\Local\AmuletTeam\AmuletMapEditor\plugins\operations`. 
        > **Important:** Copy the Operations folder path and save it somewhere to easily paste into your IDE when you choose to edit the operatons therein.
4.  **Run the Operation:** Below this menu is the **Run Operation** button. Click this to test your script on the selected region. 


## Common Issues
- **Script changed but Amulet didn’t:** Click **Refresh** in the Operation menu. If all else fails, simply close and re-open Amulet.
- **Amulet Editor not updated** If you run one of our operations and nothing seems to generate, but you're certain it should world, simply close and re-open Amulet (this seems to happen occasionally when running the Settlement generator operations).
- **Minecraft World not updated:** Remember to **Save changes** in Amulet; then re-open in Minecraft if you wish to view your generations in Minecraft itself.


**Next Steps:** Once you feel comfortable with Amulet, it's a good time to dive into learning more about our Box-Split Grammar System in the **[Box-Split Grammar Overview](./BOX-SPLIT-GRAMMAR.md)** guide.