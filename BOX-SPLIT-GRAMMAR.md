## The Box-Split Grammar

This is the core of our generation system. It works like a set of instructions that recursively divide a 3D space (a 'Selection Box') into smaller boxes. Each rule you add will tell the system how to split the selection box and what to fill it with.

**Key Concepts:**
- `BoundingBox`: The 3D selection volume that you apply rules to. It has an `origin` (the minimum x,y,z corner) and a `size` (width, height, depth).
- `@rule`: The decorator that registers a rule to our system. Each rule es on the current `BoundingBox`.
- `split()`: The primary command used to customize how our structure generates. It divides the current selection box along a specified axis (`Dimension.X`, `Dimension.Y`, or `Dimension.Z`). You must include a list of sizes for these sub-boxes.
   - **Absolute Sizes:** Positive numbers that define a fixed-size split. 
      - Example: `split(Dimension.X, [1,4,1])` splits a box into three pieces with widths of 1, 4, and 1. This would fail if the total selection box width is not exactly 6.
   - **Relative Sizes:** Negative numbers that divide up the space proportionally. 
      - Example: `split(Dimension.X, [2,-1,-2])` first creates a piece with a width of exactly 1, then divides the remaining space along that axis into two pieces, with the second piece being twice as long as the first. This is the key to creating flexible designs that can adapt to different box sizes! Here is another way to think of it: If we have 12 blocks, the first piece will have a width of exactly 2. The remaining piece that is 10 blocks will be split into two pieces: the first one being 33% (3 blocks) and the second one being 67% (7 blocks).

- `fill()`: After splitting a box up, we use the `fill()` command to place specific Minecraft blocks.
   - **Weighted Random Fill:** Instead of a single block type, we can easily fill an area with a random, weighted, set of blocks by providing a dictionary of block types and their weights. 
      - Example: `fill({"minecraft:stone_bricks": 3, "minecraft:cracked_stone_bricks": 1})` will fill an area with a 3:1 ratio of stone bricks to cracked stone bricks. 
- `void()`: A command to fill a box (or portion of a box) with air, carving out space for parts like windows, crenellations, indentations, etc.
   - Example: Creating a 2x1 window in a wall
      ```python
      with split(Dimension.Y, [-1, 2, -1]): # We split the box vertically into 3 pieces (Minecraft Y axis is up/down)
         fill("stone_bricks") # Below the window (-1)
         with split(Dimension.X, [1, 1, 1]): # We split the (2) middle rows horizontally 
            fill("stone_bricks") # Left of window
            void() # The window opening
            fill("stone_bricks") # Right of window
         fill("stone_bricks") # Above the window (-1)
      ```
- `reorient()`: A command to allow the change of the local coordinate system of the box. This allows us to dynamically change the orientation of our structure (make it face along the global X or Z axis for example), depending on the situation.
   - Example:
      ```python
      @rule
      def house():
         # Build the front wall as normal
         with split(Dimension.X, [10, -1]):
            front_facade()
            # For the side wall, reorient and reuse the same rule
            with reorient(x=Dimension.Z):
                  front_facade()
      ```
- `Iteration`: By adding `repeat=True` to a split, you can create repeating patterns. This is a great tool for features like a line of windows or columns/support beams. 
   - Example: 
      ```python 
      # Creates a repeating pattern of 1-block-wide stone pillars and 1-block-wide air gaps
      pieces = split(Dimension.X, [1, 1], repeat=True)
      while pieces:
         fill("stone"), void()
      ```
- `Probabilistic Rules`: You can create multiple definitions of the same rule by assigning each variation a probability. This is important for variation in our generations.
   - Example:
      ```python
      @rule(probability=3)
      def tower_top():
         # ... create a fancy spire ...

      @rule(probability=1)
      def tower_top():
         # ... create a flat, crenelated roof ... 
      ```
- `Rule Constraints`: You can restrict rules to only apply to boxes of certain sizes. This is great for allowing specific details of certain structures to only occur at certain selection box sizes. 
   - Example: 
      ```python
      @rule(constraint=(Dimension.X > 5))
      def wall():
         # ... logic for a wall that includes a window ...

      @rule(constraint=Constraint.ELSE)
      def wall():
         # ... logic for a solid wall, used if the above constraint fails ...
      ```

**Next Steps:** The only way to truly get comfortable with this system is to play with it yourself! Take a look at the **[Your First Structure](./BUILDING-YOUR-FIRST-STRUCTURE.md)** guide to get some hands on experience with our system.