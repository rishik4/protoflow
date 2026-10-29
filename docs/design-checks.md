# Design checks

ProtoFlow checks your design as you work. The electrical rule check (ERC) looks for wiring and connection mistakes in the schematic. The design rule check (DRC) looks for clearance, size and connection problems on the board. Fix both before you make manufacturing files.

## Schematic ERC

### How it runs

ERC runs on its own after every edit, so the results stay current while you draw. To run it on demand:

- Click **Run ERC** in the results panel.
- Choose **Run Electrical Rule Check (ERC)** in the command palette (<kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>).
- Ask the AI, or click the **Run ERC** suggestion in the AI panel.

### Where problems show up

- **On the canvas**: wires on a net with an error turn red, and a red X marks a wire end that touches a pin without connecting to it. Hover over the spot to read the message.
- **In the ERC RESULTS panel**: open it from the command palette with **Open ERC Results**. It counts **Errors**, **Warnings** and **Info**, and lists each problem with its message. Click a row to highlight the parts and wires involved and pan to them.

When everything passes, the panel says **No violations found**.

To hide the red marks, right-click the canvas and choose **Hide DRC/ERC Visuals**. **Show DRC/ERC visuals** in Settings turns them on or off for good.

### What ERC checks

| Check | Severity | What it means |
|---|---|---|
| Short Circuit | Error | Two different rails are connected, or power is connected to ground |
| Rail Pin Mismatch | Error or warning | A supply pin sits on a ground rail, or the other way round |
| Output Conflict | Error | More than one output drives the same net |
| Missing Ground | Error | A part has power but its ground pin is not connected |
| Duplicate Reference | Error | Two or more parts share a reference, such as two R1 |
| Wire Touching Unconnected | Error | A wire end touches a pin but doesn't connect to it |
| Dangling Component | Error | A part has no connections, or only one pin connected |
| Floating Pin | Warning | A pin is not connected to any net |
| No Driver | Warning | A net has inputs but nothing drives it |
| Not Annotated | Warning | Parts still have placeholder references, such as R? |
| Wire Covering Terminal | Warning | A wire passes over a pin without connecting to it |
| Wire Intersects Component | Warning | A wire runs through the body of a part |
| Component Overlap | Warning | Two parts sit on top of each other |
| Orphan Power Symbol | Warning | A power or ground symbol is connected to nothing |
| Duplicate Net Label | Warning | A pin has the same label more than once |

There is no way to waive a single ERC result. If a pin is unused on purpose, place a no-connect marker on it and the floating-pin warning goes away.

## PCB DRC

### How it runs

DRC also runs as you edit the board, checking the items each edit touched. To run a full check, click **Run Design Rule Check** in the **Output** section of the PCB toolbar. The number next to the button is the current count of problems. It is hidden when there are none.

The results open in the same panel, under **PCB Rule Check**. The panel's **Run DRC** button also compares the board with its schematic and reports missing, extra or mismatched footprints and pad nets.

### Where problems show up

Each row shows the rule that failed, such as `track-clearance` or `unconnected-net`, and a message. Click a row to select the items involved and center the view on them.

Copper clearance errors also get a red X on the board. Hover over it to read the message. You can turn these marks off with **DRC markers** in the [Layer Manager](pcb-editor.md#layer-manager).

When the board is clean, the panel says **No PCB violations found**.

### What DRC checks

| Area | Examples |
|---|---|
| Board edge | Tracks, vias, pads or holes outside the outline or too close to the edge |
| Copper clearance | Track to track, track to via, track to pad, via to via, pad to pad, copper graphics |
| Sizes and holes | Track width, via diameter and drill, annular ring, hole size, hole-to-hole spacing, copper too close to a hole |
| Keep-outs | Tracks or vias inside a keep-out area |
| Courtyards | Footprints whose courtyards overlap |
| Zones | Copper zones that could not be filled |
| Connectivity | Nets that still have unrouted connections |

## Set the rules: Board Setup

DRC uses the rules saved with each board. Click **Board Setup** in the **Output** section of the PCB toolbar. Its pages are:

| Page | What you set |
|---|---|
| **Essentials** | **Copper clearance**, **Track width**, **Via size**, **Copper layers** and **Board edge clearance** |
| **Stackup** | Board thickness and the copper, core, prepreg, mask and silkscreen layers |
| **Design Rules** | Fabrication minimums, shown on a dimensioned drawing, plus net classes |
| **Mask & Paste** | Mask and paste clearances, mask minimum web, via tenting |
| **Size Presets** | The track widths and via sizes offered while routing |
| **Boards** | Settings for layouts that hold more than one board |

On **Design Rules**, the **Fab preset** menu fills in the minimums for a board house, including JLCPCB, PCBWay, OSH Park and AISLER, or KiCad defaults. **Raise routing to minimums** updates your routing widths to match. Net classes set track width, clearance and via size for groups of nets, such as `USB_*`. Each class also has differential pair width and gap, and a current capacity tab that estimates the track width for a given current (IPC-2221).

Click **Save** to apply the changes. You can undo them in one step.

## Fix problems

1. Click the result to jump to it.
2. Fix it by hand: move the part or track, add the missing wire, or change the rule if it was too strict.
3. ERC and DRC update on their own. Run the full check again before you export.

You can also ask the AI assistant to run the checks and fix what they find. See [AI assistant](ai-assistant.md).

## Checks before export

When you export Gerbers, export DXF or order boards from the PCB toolbar while DRC still shows errors or warnings, ProtoFlow asks **Export With DRC Issues?** and lists them. Choose **Review DRC** to open the results, **Continue Anyway** to export, or **Cancel**. See [Manufacturing](manufacturing.md).

## Related

- [PCB editor](pcb-editor.md)
- [Wiring](wiring.md)
- [Power and nets](power-and-nets.md)
- [Manufacturing](manufacturing.md)
