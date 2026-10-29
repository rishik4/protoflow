# Footprint editor

The footprint editor is where you draw the copper pads and outlines a part sits on. You can place pads one by one, generate a standard package from a few numbers, make pad arrays, draw silkscreen and courtyard, and check the result before it goes on a board.

## Open a footprint

Footprints open in their own editor tab. You can start one from several places:

| From | How |
|---|---|
| A new, blank footprint | **File > New > Footprint**, the **+** menu in the tab strip, or **New Footprint** in the command palette |
| A part on the board | Right-click it in the PCB editor and choose **Edit Footprint** |
| A part in your library | Click **Edit footprint** in the part preview of the component picker |
| A schematic part | Select it and use **Open footprint**, **Create** or **Replace** in the Properties panel |
| A symbol you are drawing | Use the **Footprint** section of the symbol editor's Properties panel |
| The AI Component Lab | Click **Draw** to draw the footprint yourself. See [Component Lab](component-lab.md). |

A blank footprint starts with reference text and a small silkscreen rectangle, and no pads.

The editor opens with a 0.5 mm grid and snap on. All dimensions are in millimetres.

## Tools

Pick a tool from the toolbar or press its key. The canvas needs focus for the keys to work, so click it first.

| Tool | Key | How it works |
|---|---|---|
| Select | <kbd>S</kbd> | Click or drag to select. <kbd>Esc</kbd> also returns to Select. |
| Pan | <kbd>Space</kbd> | Switches to the pan tool. You can also drag with the middle or right mouse button. |
| Pad | <kbd>P</kbd> | Click to place a pad |
| Line | <kbd>L</kbd> | Click the start, then click the end |
| Arc | <kbd>A</kbd> | Click the start, the end, then a point on the arc |
| Rectangle | <kbd>G</kbd> | Click one corner, then the opposite corner |
| Circle | <kbd>C</kbd> | Click the center, then click to set the size |
| Polygon | <kbd>O</kbd> | Click each point, then double-click or press <kbd>Enter</kbd> |
| Text | <kbd>T</kbd> | Click to place text |
| Measure | <kbd>M</kbd> | Click two points |

## Edit what you placed

| Action | Key |
|---|---|
| Open properties | <kbd>E</kbd>, or double-click the item |
| Rotate 90° one way or the other | <kbd>R</kbd> and <kbd>Shift</kbd>+<kbd>R</kbd> |
| Mirror horizontally / vertically | <kbd>H</kbd> / <kbd>V</kbd> |
| Duplicate | <kbd>D</kbd> or <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>D</kbd> |
| Nudge by one grid step (×10 with <kbd>Shift</kbd>) | Arrow keys |
| Delete | <kbd>Delete</kbd> or <kbd>Backspace</kbd> |
| Cut, copy, paste | <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>X</kbd>, <kbd>C</kbd>, <kbd>V</kbd> |
| Select all | <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>A</kbd> |
| Undo / redo | <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Z</kbd> / <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>Z</kbd> |
| Zoom to fit | <kbd>Home</kbd> or <kbd>0</kbd> |

Right-click for the same actions plus **Push Pad Properties to Other Pads** (on a pad), **Create Pad Array…** and **Footprint Properties…**.

## Pads

Double-click a pad to open **Pad Properties**.

| Setting | Options |
|---|---|
| **Pad type** | **SMD**, **Through-hole**, **NPTH, Mechanical**, **Edge Connector** |
| **Pad shape** | **Circular**, **Oval**, **Rectangular**, **Rounded Rectangle**, **Trapezoidal** |
| Position, size, rotation | In millimetres and degrees. Rounded rectangles also take a **Corner ratio (%)** and an optional chamfer per corner. |
| Drill | For through-hole and NPTH pads: **Hole size (mm)**, or a slot with **Slot (oblong)**, plus an optional offset of the pad from the hole |
| **Layers** | Copper, paste, mask and silkscreen layers, front, back or both |
| **Fabrication property** | **None**, **BGA pad**, **Fiducial, local to footprint**, **Fiducial, global to board**, **Test point pad**, **Heatsink pad**, **Castellated pad**, **Mechanical** |
| **Clearance Overrides** | Clearance, mask expansion and paste settings for this pad. Leave blank to use the footprint or board value. |
| **Copper Zone Connection** | **From parent footprint**, **Solid**, **Thermal relief** or **None**, plus relief gap and spoke width |

New pads copy the settings of the last pad you edited. A pad with paste layers only and no number works as a paste aperture, for example to split the paste on a thermal pad.

## Generate a standard package

For common packages you don't need to place pads by hand. Click **Generate Footprint** in the toolbar to open **Generate Footprint (parametric)**. Pick a family, enter the numbers from the datasheet, and click **Generate**.

Families:

- Chip (0402..2512 / SOD / MELF)
- SOIC / SOP / SSOP / TSSOP
- SOT-23 (3/5/6/8)
- SOT-223 / DPAK
- QFP / LQFP / TQFP
- QFN / DFN / SON (+ exposed pad)
- DIP (through-hole)
- Pin header / SIP (through-hole)
- BGA / LGA

You enter the pad count, pitch, row span, pad size, body size and drill as the family needs. QFN parts take an optional thermal pad size, and BGA parts an optional grid size. The generator builds the pads, courtyard and outlines, and replaces what is in the editor. Undo brings the old footprint back.

## Pad arrays

Press <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>T</kbd> with the canvas focused, or choose **Create Pad Array…**.

- **Grid Array**: columns, rows, X and Y pitch, and a start number. Numbering is **Continuous (1, 2, 3...)** or **Coordinate (A1, A2... B1)**, the BGA option. BGA letters skip I, O, Q, S, X and Z, as JEDEC does.
- **Circular Array**: pad count, radius, start angle and start number. **Rotate pads with position** turns each pad to face outward.

New pads use the current pad settings. Edit one pad first if you want different ones.

## Silkscreen, courtyard and fab layers

New lines, shapes and text go on the active layer. Pick it from the **Layer:** list in the status bar at the bottom of the canvas. The default is F.SilkS.

| Layers | Use |
|---|---|
| F.SilkS / B.SilkS | Silkscreen outline, pin 1 mark and labels |
| F.CrtYd / B.CrtYd | Courtyard, the area kept clear around the part |
| F.Fab / B.Fab | The real body outline, for documentation |

Copper, mask, paste, Dwgs.User, Cmts.User and Edge.Cuts are also available.

**Generate Courtyard + Fab outline** in the toolbar draws both for you: a courtyard 0.25 mm outside the pads and graphics, as the KiCad library convention recommends, and a fab outline around the part.

## Footprint properties

Click **Footprint Properties…** in the toolbar, or double-click an empty part of the canvas.

- **Footprint name**, **Reference**, **Value**, **Description** and **Keywords**
- **Attributes**: **Unspecified**, **SMD** or **Through hole**
- **Exclude from position files**, **Exclude from BOM**, **Not in schematic (board only)**, **Exempt from courtyard requirement**, **Do not populate** and **Locked**
- **Clearance Overrides** for the whole footprint
- **3D Models**: click **+** and enter the path to a model file. Use **Show** to turn a model on or off.

## Check the footprint

Click **Footprint Checker** in the toolbar. The **Footprint Checker** dialog lists errors and warnings, or says **No problems found.** It looks for:

- A missing courtyard
- Pads with no size, through-hole pads without a hole, and SMD pads with one
- Annular rings below 0.15 mm, or a hole that leaves no copper
- Pads with different numbers that overlap and would short
- Silkscreen lines that cross pads
- A component type that doesn't match the pads
- Copper pads with no number
- A hidden or missing reference designator

## Save

Click **Apply** in the toolbar or press <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>S</kbd>. Where the change goes depends on where you opened the footprint:

- From a part on the board: only that placed footprint is updated. The board needs to be open.
- From a library part: the part's own footprint file is updated.
- From the Component Lab: the footprint goes back to the Lab.
- A new footprint: it is saved to your personal footprint library and linked to the part, if there is one.

## Related

- [PCB editor](pcb-editor.md)
- [Symbol editor](symbol-editor.md)
- [Component Lab](component-lab.md)
- [Components and parts](components-and-parts.md)
