# Symbol editor

The symbol editor is where you draw schematic symbols: the body outline, the pins, and the text. Symbols are stored as KiCad `.kicad_sym` files, so they work in KiCad too.

## Open the symbol editor

- To start a new symbol, choose **File > New > Symbol**. The new symbol starts with a rectangle body, the reference prefix `U` and no pins.
- To edit the symbol of a library part on your schematic, double-click the part.
- To edit a part from the parts catalog or your library, select it in the **Place Component** window and choose **Edit symbol** in **Part Preview**.

The symbol opens in its own tab. The toolbar switches to the symbol tools, and the **Properties** panel shows the selected item. The **Symbol Libraries** panel lists the libraries of the symbol you have open.

## Draw the body

| Tool | Shortcut | How to draw |
| --- | --- | --- |
| Rectangle | <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>R</kbd>, or <kbd>R</kbd> with nothing selected | Drag from corner to corner |
| Triangle | Toolbar only | Drag from corner to corner |
| Circle | <kbd>C</kbd> | Click the center, then a point on the edge |
| Lines/Polygon | <kbd>L</kbd> | Click each point, then press <kbd>Enter</kbd> or double-click |
| Arc | <kbd>A</kbd> | Click the start, the end, then a point on the arc |
| Bezier | <kbd>B</kbd> | Click the start, the end, then two control points |
| Text | <kbd>T</kbd> | Click to place, then enter the text in the dialog |

Press <kbd>Esc</kbd> to cancel a shape you are drawing and return to the **Select** tool. The **Insert text box or imported graphics** button adds a text box, or imports outlines from an SVG or DXF file and scales them to the size you enter.

## Add pins

1. Press <kbd>P</kbd>, or click **Add Pin**.
2. Choose which way the pin points with **Pin Left**, **Pin Right**, **Pin Up** or **Pin Down** in the toolbar. While the pin tool is active, <kbd>R</kbd> also turns the pin direction.
3. Click to place the pin.
4. Press <kbd>Insert</kbd> to add the next pin. It repeats the last pin one step further along and counts up the pin number. To change the step and the number increment, open **More symbol settings** and choose **Repeat pin settings…**.

To edit a pin, select it and press <kbd>E</kbd>. **Pin Properties** has these settings:

| Setting | What it sets |
| --- | --- |
| **Pin name** | The label on the symbol, for example `VCC` or `SDA`. Write `~{RESET}` to draw a bar over the name. |
| **Pin number** | The pad number the pin connects to on the footprint. |
| **Name size**, **Number size** | Text sizes. |
| **X position**, **Y position**, **Length** | Where the pin sits and how long it is. |
| **Electrical type** | **Input**, **Output**, **Bidirectional**, **Tri-State**, **Passive**, **Free**, **Unspecified**, **Power Input**, **Power Output**, **Open Collector**, **Open Emitter** or **Unconnected**. The electrical rules check uses this. |
| **Graphic style** | How the pin is drawn: **Line**, **Inverted**, **Clock**, **Inverted Clock**, **Input Low**, **Clock Low**, **Output Low**, **Falling Edge Clock** or **Non-Logic**. |
| **Orientation** | Which way the pin points. |
| **Visible** | Show or hide the pin. |
| **Alternate pin functions** | Extra functions one physical pin can take. |

To edit many pins at once, click **Pin Table (bulk edit pins)** in the toolbar.

## Select and edit

| Action | Shortcut |
| --- | --- |
| Select tool | <kbd>S</kbd> |
| Edit properties of the selection | <kbd>E</kbd> |
| Move and place | <kbd>M</kbd> |
| Duplicate and place | <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>D</kbd> |
| Rotate counterclockwise | <kbd>R</kbd> |
| Rotate clockwise | <kbd>Shift</kbd>+<kbd>R</kbd> |
| Mirror horizontally | <kbd>X</kbd> |
| Mirror vertically | <kbd>Y</kbd> |
| Move, rotate or scale by exact amounts | <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>M</kbd> |
| Nudge | Arrow keys |
| Delete | <kbd>Delete</kbd> |

Commands that act on a selection also work on the item under the cursor when nothing is selected. Other tools in the toolbar:

- **Align and distribute selection** lines up or spaces out several items.
- **Selection filters** limit selection to **Pins**, **Shapes**, **Text** or **Hidden items**.
- **Display, grids and navigation** has options such as **Lasso selection**, **Show fields**, cursor style, and **Navigation and panning…**, where you can choose how the mouse wheel and trackpad pan and zoom.

## Grid and view

| Action | Shortcut |
| --- | --- |
| Show or hide the grid | <kbd>G</kbd> |
| Snap to grid | <kbd>Shift</kbd>+<kbd>G</kbd> |
| Next or previous grid size | <kbd>N</kbd> / <kbd>Shift</kbd>+<kbd>N</kbd> |
| Fast grid 1 or 2 | <kbd>Alt</kbd>+<kbd>1</kbd> / <kbd>Alt</kbd>+<kbd>2</kbd> |
| Use item-specific grids for pins, graphics and text | <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>G</kbd> |
| Zoom in or out | <kbd>=</kbd> / <kbd>-</kbd>, or the mouse wheel |
| Zoom to fit | <kbd>Home</kbd> |
| Zoom to selection | <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Home</kbd> |
| Measure a distance | <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>I</kbd> |
| Reset relative coordinates at the cursor | <kbd>Space</kbd> |

Drag with the middle mouse button to pan. **Show Hidden Pins** and **Show Pin Electrical Types** in the toolbar help you check your pins.

## Multi-unit symbols

A symbol can have several units, such as the four gates of a quad op-amp, and alternate body styles. Use the **Units and body styles** menu in the toolbar to **Add empty unit**, **Duplicate current unit**, **Delete current unit**, **Add empty body style**, **Duplicate body style**, **Name body style…** or **Delete current body style**. Turn on **Synchronize pin edits across units** to keep shared pins in step.

## Properties, checks and export

- **Symbol Properties (fields, attributes, filters)** edits the symbol's fields, such as reference, value, footprint and datasheet.
- **Check Symbol (duplicate pins, off-grid pins, ...)** lists problems in every unit and body style.
- **Export or print symbol** saves a KiCad symbol (`.kicad_sym`), an SVG, a PNG, or a PDF for printing.
- **More symbol settings** has **Symbol fields…**, **Attributes, attachments and simulation model…**, **Manage symbol libraries…**, **Set symbol anchor…** and **Repeat pin settings…**.

## Save the symbol

Click **Apply** in the toolbar, or press <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>S</kbd>.

- A new symbol is saved to your Custom Library as a `.kicad_sym` file.
- A symbol from a library is saved back to its `.kicad_sym` file.
- For a symbol you opened from the schematic, choose **Save to this instance** to change only that part, or **Save to instance + library** to update the library symbol as well.

If other placed parts use an older copy of the symbol, ProtoFlow offers **Update all** to bring them up to date.

## Change the shortcuts

Open **Editing actions and shortcuts** in the toolbar and choose **Configure shortcuts…**. Click a shortcut and press the new key combination. In the same dialog you can **Restore defaults**, or use **Import…** and **Export…** to share your shortcut set.

## Related

- [Components and parts](components-and-parts.md)
- [Footprint editor](footprint-editor.md)
- [Component Lab](component-lab.md)
- [Keyboard shortcuts](keyboard-shortcuts.md)
