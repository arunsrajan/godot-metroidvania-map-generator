# 🗺️ MetSys Metroidvania Map Generator & Editor — User Guide

The **MetSys Metroidvania Map Generator & Editor** is an interactive, browser-based procedural map generation and editing tool built specifically for KoBeWi's [Metroidvania-System (MetSys)](https://github.com/KoBeWi/Metroidvania-System) for Godot 4.

---

## 🌟 Key Features

### 1. MetSys Specification & Multi-Layer System
* **Seamless Room Merging**: Contiguous cells of the same color automatically form a single room. Interior grid lines are hidden, and internal borders are set to `-1` (`OPEN`), exactly adhering to MetSys rules.
* **Multi-Layer Support**: Create, manage, and toggle between multiple map layers (`Layer 0`, `Layer 1`, etc.) with ghost layer overlay rendering.

### 2. Procedural Map Generation
* **Seed-Based Generation**: Reproducible map layouts using custom text or numeric seeds.
* **Presets**: Pre-configured style presets including *Classic Metroid*, *Castlevania*, and *Hollow Knight Style*.
* **Customizable Parameters**: Control map dimensions, area padding, connection distance, ability gate counts, save/warp room density, secret room chance, and exploration loop shortcuts.

### 3. Interactive Canvas & Navigation
* **Intuitive Drag-to-Pan**: Click and drag anywhere on the canvas (Left-Click drag, Middle-Click drag, or Right-Click drag) to pan the map view smoothly.
* **Mouse Wheel Zoom & Controls**: Zoom in/out with the mouse wheel or toolbar buttons (`➕`, `➖`, `🎯 Fit`, `1:1`). `🎯 Fit` automatically centers and fits all map rooms on screen.
* **Hover Inspector**: Real-time tooltip showing cell coordinates `[X, Y, Z]`, Area Name/ID, Room ID, Cell Type, Symbols, Borders `[R, D, L, U]`, and assigned Godot scene path.

### 4. Editing Tools (Toolbar)
* 🔍 **Inspect**: Click any room to view its details and highlight it in the sidebar inspector.
* 🖌️ **Paint Area**: Paint cells to assign them to the selected area color.
* 🚪 **Toggle Door**: Click borders to cycle door/passage types (Solid Wall, Standard Passage, Missile/Red Door, Blue Door, Super Missile/Green Door, Power Bomb/Yellow Door, One-Way Passage, Boss Gate).
* ⭐ **Place Symbol**: Place MetSys map icons (Save Points, Warps, Bosses, Major Abilities, Items/Collectibles, Shops, NPCs, Secrets, Start Points).
* 🎬 **Assign Scene**: Click any room to open the **Godot Scene Picker Modal** to select or enter a `res://` Godot scene file.
* 🧹 **Erase**: Remove individual cells or entire rooms (`Shift + Click`).

### 5. Godot Project & Scene Management (`🎬 Scenes` Tab)
* **Godot Project Root Folder Scanner**: Select your base Godot project folder. Automatically scans all `.tscn` and `.scn` files and formats them as relative `res://` paths.
* **In-Tab Room Inspector**: View the inspected room's coordinates, area, size, and current assigned scene inside the *Godot Project Root Folder* section.
* **Scene Picker Modal**: Opened by clicking a room with the `Assign Scene` tool active. Features real-time search, 1-click selection, double-click assignment, and custom path entry.
* **Auto-Assigners**:
  * *Auto-Assign by Pattern*: Formats paths using template placeholders (`res://scenes/rooms/{area_name}_{room_id}.tscn`).
  * *Auto-Match from Project Files*: Automatically pairs map rooms with discovered project `.tscn` files.
* **Assigned Scenes List**: Interactive list of all assigned rooms with 1-click room inspection.

### 6. Layer & Area Management (`🥞 Layers & Areas` Tab)
* Add, rename, reorder, and remove map layers.
* Create and configure custom areas with custom color pickers and room targets.

### 7. Import & Export (`💾 Import/Export` Tab)
* **MapData.txt Export & Import**: Full support for official MetSys text data export (`MapData.txt`). Guaranteed filename download (`MapData.txt`).
* **JSON Export & Import**: Native JSON format for full project state backup and restore.
* **PNG Map Image Export**: Export crisp, high-resolution PNG map previews (`MapData_Preview.png`).
* **Live Text Editor**: View and modify the raw `MapData.txt` text directly in the browser.

### 8. Validation & Live Statistics (`✅ Validation` Tab)
* **Real-time Statistics**: Live counters for total rooms, cells, areas, passages, save points, and secrets.
* **Rule Checker**: Validates room color consistency, scene assignment consistency, border symmetry, invalid symbols, and open passages facing empty space.

---

## 🚀 How to Use the Tool

### Step 1: Generate or Import a Map
1. **Procedural Generation**:
   * Navigate to the **⚙️ Generation** tab.
   * Select a preset (e.g., *Castlevania*) or adjust sliders (Area Padding, Loop Factor, etc.).
   * Click **⚡ Generate All Layers** to build the map layout.
2. **Import Existing MapData**:
   * Navigate to the **💾 Import/Export** tab.
   * Click **Choose File** under *Import MetSys MapData.txt* or paste content into the raw text area and click **Import Text Data**.

### Step 2: Navigate & Edit the Map
1. **Pan & Zoom**:
   * **Pan**: Left-click and drag anywhere on the canvas to move the view.
   * **Zoom**: Use the mouse wheel or click **🎯 Fit** in the toolbar to center all map cells.
2. **Edit Doors & Symbols**:
   * Select **🚪 Toggle Door** from the toolbar and click cell edges to change door types.
   * Select **⭐ Place Symbol** from the toolbar and click cells to place Save Points, Warps, Items, or Boss icons.

### Step 3: Connect Your Godot Project & Assign Scenes
1. Navigate to the **🎬 Scenes** tab.
2. Click **📁 Select Godot Project Folder** and choose your Godot project root directory.
3. **Assign Scenes**:
   * Select the **🎬 Assign Scene** tool from the canvas toolbar.
   * Click any room on the map.
   * The **Scene Picker Popup Modal** will open. Select a `.tscn` file from your project list (or type a custom path) and click **Assign Scene to Room**.
   * Alternatively, click **Auto-Match from Project .tscn Files** in the Scenes tab to auto-link matching rooms.

### Step 4: Export to MetSys
1. Navigate to the **💾 Import/Export** tab.
2. Click **📥 Download MapData.txt** to save the map file into your Godot project root (or `res://` directory).
3. MetSys in Godot will read `MapData.txt` to construct your in-game Metroidvania map and load room scenes!
