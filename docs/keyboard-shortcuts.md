# Keyboard shortcuts

This page lists the keyboard shortcuts in ProtoFlow, grouped by editor. Where a shortcut differs between platforms, the macOS key comes first: <kbd>Cmd</kbd>/<kbd>Ctrl</kbd> means <kbd>Cmd</kbd> on macOS and <kbd>Ctrl</kbd> on Windows and Linux, and <kbd>Option</kbd>/<kbd>Alt</kbd> works the same way.

Single-letter shortcuts work when the canvas has focus, not while you are typing in a text field. To see a short list inside the app, choose **Help > Keyboard Shortcuts**. The command palette also shows each command's shortcut.

## General

| Shortcut | Action |
| --- | --- |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>S</kbd> | Save |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>T</kbd> | New project |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> | Open the command palette |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>W</kbd> | Close the current tab |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>T</kbd> | Reopen the last closed tab |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>1</kbd> to <kbd>8</kbd> | Go to tab 1 to 8 |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>9</kbd> | Go to the last tab |
| <kbd>Esc</kbd> | Cancel the current action or clear the selection |

## Schematic editor

### Tools

| Shortcut | Action |
| --- | --- |
| <kbd>S</kbd> | Select tool |
| <kbd>W</kbd> | Wire tool |
| <kbd>L</kbd> | Net label tool |
| <kbd>T</kbd> | Text tool |
| <kbd>Ctrl</kbd>+<kbd>Space</kbd> | Place Component (use <kbd>Ctrl</kbd> on macOS too) |
| <kbd>F5</kbd> | Run or stop the simulation |

### Quick-place parts

These are the default keys. You can change them, and give your own parts a key, in the **Components** panel. See [Components and parts](components-and-parts.md#assign-your-own-keys).

| Shortcut | Places |
| --- | --- |
| <kbd>R</kbd> | Resistor (when nothing is selected) |
| <kbd>C</kbd> | Capacitor |
| <kbd>I</kbd> | Inductor |
| <kbd>O</kbd> | Op-amp |
| <kbd>V</kbd> | VCC |
| <kbd>D</kbd> | GND |
| <kbd>5</kbd> | +5V |
| <kbd>3</kbd> | +3.3V |
| <kbd>X</kbd> | No-connect marker |

### Editing

| Shortcut | Action |
| --- | --- |
| <kbd>R</kbd> | Rotate the selection, or the part you are placing, clockwise |
| <kbd>Shift</kbd>+<kbd>R</kbd> | Rotate counterclockwise |
| <kbd>M</kbd> | Mirror the selection |
| <kbd>P</kbd> | Open **Properties** for the selected parts |
| <kbd>V</kbd> | Show or hide the selected reference or value text |
| Arrow keys | Nudge the selection one grid step |
| <kbd>Shift</kbd>+arrow keys | Nudge the selection five grid steps |
| <kbd>Delete</kbd> or <kbd>Backspace</kbd> | Delete the selection |
| <kbd>Shift</kbd>+<kbd>Delete</kbd> | Delete the selection and its connected wires |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>A</kbd> | Select all |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>C</kbd> | Copy |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>X</kbd> | Cut |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>V</kbd> | Paste. The items follow the cursor until you click. |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Z</kbd> | Undo |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>Z</kbd> or <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Y</kbd> | Redo |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>F</kbd> | Find a component or net |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>J</kbd> | Auto Connect the selected parts, left to right |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>J</kbd> | Auto Connect, then clean up |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>U</kbd> | Clean up the schematic |

### While drawing a wire

| Shortcut | Action |
| --- | --- |
| <kbd>Space</kbd> or <kbd>/</kbd> | Flip the corner between horizontal-first and vertical-first |
| <kbd>Backspace</kbd> or <kbd>Delete</kbd> | Remove the last segment |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Z</kbd> | Remove the last segment |
| <kbd>Esc</kbd> | Cancel the wire |

### View

| Shortcut | Action |
| --- | --- |
| <kbd>+</kbd> / <kbd>-</kbd> | Zoom in or out |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>0</kbd> | Reset zoom |
| <kbd>G</kbd> | Show or hide the grid |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>G</kbd> | Turn grid snap on or off |
| Middle mouse drag | Pan |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+drag | Pan |

## PCB editor

### Tools

| Shortcut | Action |
| --- | --- |
| <kbd>S</kbd> | Select tool |
| <kbd>W</kbd> or <kbd>X</kbd> | Route a track. If the cursor is over a pad or track, routing starts there. |
| <kbd>6</kbd> | Route a differential pair |
| <kbd>V</kbd> | Via tool. While routing, adds a via. |
| <kbd>Z</kbd> | Copper zone tool |
| <kbd>K</kbd> | Keepout tool |
| <kbd>T</kbd> | Text tool |
| <kbd>M</kbd> | Measure tool |
| <kbd>O</kbd> | Edit the board outline |
| <kbd>P</kbd> | Properties of the selection. With nothing selected, the Pan tool. |
| <kbd>E</kbd> | Properties of the selection |
| <kbd>L</kbd> | Open the layer manager. While routing, change the corner style. |

### Layers and view

| Shortcut | Action |
| --- | --- |
| <kbd>1</kbd> / <kbd>2</kbd> | Top or bottom copper layer |
| <kbd>3</kbd> / <kbd>4</kbd> | Inner layer 1 or 2 |
| <kbd>Page Up</kbd> or <kbd>*</kbd> | Next copper layer |
| <kbd>Page Down</kbd> | Previous copper layer |
| <kbd>Option</kbd>/<kbd>Alt</kbd>+<kbd>3</kbd> | Switch between the 2D and 3D board view |
| <kbd>H</kbd> | Change how strongly inactive layers are dimmed |
| <kbd>`</kbd> | Turn net highlighting on or off |

While routing, the layer keys add a via and continue on the new layer.

### Routing

| Shortcut | Action |
| --- | --- |
| <kbd>Space</kbd> or <kbd>/</kbd> | Flip the corner direction |
| <kbd>+</kbd> / <kbd>-</kbd> | Make the trace wider or narrower |
| <kbd>Backspace</kbd> or <kbd>Delete</kbd> | Undo the last route point |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Z</kbd> | Undo the last route point |
| <kbd>Enter</kbd> or <kbd>End</kbd> | Finish the route at the cursor |
| <kbd>Esc</kbd> | Stop the route. Press again to leave the routing tool. |
| <kbd>D</kbd> | Drag the track segment under the cursor |

### Editing

| Shortcut | Action |
| --- | --- |
| <kbd>R</kbd> | Rotate the selected footprints or graphics |
| <kbd>F</kbd> | Flip the selected footprints to the other side of the board |
| Arrow keys | Nudge the selection |
| <kbd>Delete</kbd> or <kbd>Backspace</kbd> | Delete the selection |
| <kbd>U</kbd> | Select the tracks connected to the selected or hovered track |
| <kbd>I</kbd> | Select all copper on the selected or hovered net |
| <kbd>B</kbd> | Fill copper zones |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>B</kbd> | Unfill copper zones |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>A</kbd> | Select all |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>D</kbd> | Duplicate the selection |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>F</kbd> | Find a footprint or net |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>L</kbd> | Lock or unlock the selected footprints |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Z</kbd> | Undo |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>Z</kbd> or <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Y</kbd> | Redo |

## Symbol editor

You can change any of these in the symbol editor. See [Symbol editor](symbol-editor.md#change-the-shortcuts).

| Shortcut | Action |
| --- | --- |
| <kbd>S</kbd> | Select tool |
| <kbd>P</kbd> | Add pin |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>R</kbd> | Draw rectangle |
| <kbd>C</kbd> | Draw circle |
| <kbd>L</kbd> | Draw lines or polygon |
| <kbd>A</kbd> | Draw arc |
| <kbd>B</kbd> | Draw Bezier curve |
| <kbd>T</kbd> | Add text |
| <kbd>E</kbd> | Edit item properties |
| <kbd>M</kbd> | Move the selection |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>D</kbd> | Duplicate and place |
| <kbd>R</kbd> | Rotate counterclockwise. With nothing selected, draw a rectangle. |
| <kbd>Shift</kbd>+<kbd>R</kbd> | Rotate clockwise |
| <kbd>X</kbd> | Mirror horizontally |
| <kbd>Y</kbd> | Mirror vertically |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>M</kbd> | Move, rotate or scale by exact amounts |
| <kbd>Insert</kbd> | Repeat the last item |
| <kbd>Delete</kbd> | Delete |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>C</kbd> / <kbd>X</kbd> | Copy or cut |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>V</kbd> | Paste and place |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>A</kbd> | Select all |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>A</kbd> | Clear the selection |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Z</kbd> | Undo |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>Z</kbd> | Redo |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>I</kbd> | Measure a distance |
| <kbd>Space</kbd> | Reset relative coordinates at the cursor |
| <kbd>=</kbd> / <kbd>-</kbd> | Zoom in or out |
| <kbd>Home</kbd> | Zoom to fit |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Home</kbd> | Zoom to the selection |
| <kbd>G</kbd> | Show or hide the grid |
| <kbd>Shift</kbd>+<kbd>G</kbd> | Turn grid snap on or off |
| <kbd>N</kbd> / <kbd>Shift</kbd>+<kbd>N</kbd> | Next or previous grid size |
| <kbd>Option</kbd>/<kbd>Alt</kbd>+<kbd>1</kbd> / <kbd>2</kbd> | Fast grid 1 or 2 |
| <kbd>Option</kbd>/<kbd>Alt</kbd>+<kbd>4</kbd> | Switch between the fast grids |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>G</kbd> | Turn item-specific grids on or off |
| Arrow keys | Nudge the selection |
| <kbd>Enter</kbd> | Finish the shape you are drawing |
| <kbd>Esc</kbd> | Cancel and return to the Select tool |

## Footprint editor

| Shortcut | Action |
| --- | --- |
| <kbd>S</kbd> | Select tool |
| <kbd>P</kbd> | Add pad |
| <kbd>L</kbd> | Add line |
| <kbd>A</kbd> | Add arc |
| <kbd>G</kbd> | Add rectangle |
| <kbd>C</kbd> | Add circle |
| <kbd>O</kbd> | Add polygon |
| <kbd>T</kbd> | Add text |
| <kbd>M</kbd> | Measure |
| <kbd>Space</kbd> | Pan tool |
| <kbd>E</kbd> | Properties of the selection |
| <kbd>D</kbd> or <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>D</kbd> | Duplicate the selection |
| <kbd>R</kbd> | Rotate the selection clockwise |
| <kbd>Shift</kbd>+<kbd>R</kbd> | Rotate the selection counterclockwise |
| <kbd>H</kbd> | Mirror horizontally |
| <kbd>V</kbd> | Mirror vertically |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>T</kbd> | Create a pad array |
| Arrow keys | Nudge the selection. Hold <kbd>Shift</kbd> for ten times the step. |
| <kbd>Home</kbd> or <kbd>0</kbd> | Zoom to fit |
| <kbd>Enter</kbd> | Finish the polygon you are drawing |
| <kbd>Delete</kbd> or <kbd>Backspace</kbd> | Delete the selection |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>C</kbd> / <kbd>X</kbd> / <kbd>V</kbd> | Copy, cut or paste |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>A</kbd> | Select all |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Z</kbd> | Undo |
| <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>Z</kbd> | Redo |
| <kbd>Esc</kbd> | Cancel the shape, return to the Select tool, then clear the selection |

## AI chat

| Shortcut | Action |
| --- | --- |
| <kbd>Enter</kbd> | Send your message |
| <kbd>Enter</kbd> while the AI is working | Queue your message to send when the AI finishes |
| <kbd>Shift</kbd>+<kbd>Enter</kbd> while the AI is working | Interrupt the AI and send your message now |

To swap the last two, open Settings, go to **Input**, and turn on **Swap queue / steer shortcuts**.

## Related

- [Schematic editor](schematic-editor.md)
- [Wiring](wiring.md)
- [PCB editor](pcb-editor.md)
- [Symbol editor](symbol-editor.md)
