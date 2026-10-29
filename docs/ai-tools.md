# What the AI can do

This page lists what ProtoFlow's AI can do for you, grouped by the part of the design it works on. You don't call these abilities yourself: describe what you want in the AI Copilot and the AI picks the right steps. For how to use the panel, see [AI assistant](ai-assistant.md).

What the AI can do depends on the mode:

- **Standard** builds and edits the schematic or board in the tab you have open.
- **Ask** only reads. It answers questions and never changes the design.
- **Max (Studio)** does everything Standard does across a whole project, plus parts selection, checks and outputs. See [Max mode](max-mode.md).

## Schematic

### Build a new schematic

On an empty schematic, describe the circuit and Standard mode builds it in one pass:

- Chooses catalog parts (with LCSC numbers) and generic resistors and capacitors.
- Places them, wires them with wires or net labels, and adds power and ground symbols, no-connect markers and decoupling capacitors.
- Groups the parts into labeled sections, such as power, MCU and connectors.
- Looks up datasheets and reference information while it plans.
- Runs the electrical rules check at the end.

![The AI building a schematic from a prompt](media/ai-generate-board.gif)

If the catalog has no match for a part, the chat shows a card offering to create a custom part, for example in the [Component Lab](component-lab.md).

### Edit an existing schematic

On a schematic that already has parts, Standard mode makes targeted edits:

- Change component values.
- Remove parts, with or without their support parts, and reconnect around them.
- Connect pins to a net, or disconnect them.
- Add a part in series or a pull-up or pull-down resistor.
- Rename nets.
- Swap generic passives.
- Add power symbols to pins and wire decoupling capacitors.
- Clean up dangling wires and labels.
- Add new circuitry to the sheet.

Standard mode's edits don't move or rotate existing parts or add notes and shapes. Do those by hand in the [Schematic editor](schematic-editor.md).

The AI keeps its edits to the parts you asked about. If a change has to reach further, it stops on a **Waiting for your approval** card that explains why, and continues only if you approve.

## PCB

On a board tab, Standard mode works on placement, shape and routing:

- **Placement:** put parts in regions or along edges, in rows, rings or groups, on the top or bottom side, and fit them to the board size.
- **Board shape:** change the outline to a rectangle, rounded rectangle, circle, regular polygon (such as a hexagon) or star.
- **Routing:** route the board or selected nets, and remove routing.
- **Board setup:** set the layer count and stackup, add copper planes, apply net classes, and set up high-speed interfaces and differential pairs before routing.
- **Fixing problems:** look at unrouted nets and design rule errors, move, rotate or flip parts, reroute, repair planes, add ground stitching vias, and add or edit copper zones and keep-out areas.

The AI only reports a board as done after it checks the airwires and runs a full design rules check. If something is left, it says what.

If a board change needs a schematic change, the AI asks first and edits nothing until you agree. Editing individual traces by hand and exporting fabrication files are not AI tasks in Standard mode. Use the [PCB editor](pcb-editor.md) and [Manufacturing](manufacturing.md) tools.

## Parts

- **Search the catalog.** The AI finds real parts and shows part cards with a photo, price and a datasheet link.
- **Read datasheets.** It looks up a part's datasheet, or reads a PDF you attach. See [Datasheet viewer](datasheet-viewer.md).
- **Make a missing part.** In the [Symbol editor](symbol-editor.md) and [Footprint editor](footprint-editor.md), the AI can generate a symbol or footprint from a datasheet. The [Component Lab](component-lab.md) does both halves at once.
- **Respect locked parts.** If you right-click a part and choose **Lock in Place**, the AI asks before it moves or changes it. Click **Unlock & continue** to let it, or **Keep locked** to protect the part.

## Checks and reviews

- **Electrical rules check.** Builds and edits finish with an electrical rules check.
- **Design review.** Ask Standard mode to review your circuit, for example "Review my schematic for problems." It checks the schematic part by part and shows a **Schematic review** card with one finding per issue. On a finding, click **Fix** to have the AI fix it, **New chat** to discuss it in a new conversation, or **Dismiss** to hide it. The review itself changes nothing.
- **Board check.** On a board, the AI runs the design rules check and lists unrouted connections.

See [Design checks](design-checks.md) for running these checks yourself.

## Questions and answers

**Ask** mode, and questions you type in Standard mode, can:

- Explain what a circuit or part of it does.
- Trace which pins and parts are on a net.
- Search and read attached datasheets.
- Search the web and read pages you link.
- Draw a block diagram. Diagrams appear as flowcharts in the chat, and you can open one as its own diagram tab to edit.

When the AI needs a decision from you, it shows a question card with a few options, one marked as recommended. See [AI assistant](ai-assistant.md#questions-from-the-ai).

## Max mode only

[Max mode](max-mode.md) adds:

- Choosing every part for a board, with stock checks and alternatives, and importing each part's symbol, footprint and 3D model.
- Schematic, placement, routing and checks for a whole board in one run.
- Fabrication outputs when you ask: Gerbers, drill files, pick-and-place, an assembly BOM and a STEP model.
- BOM and netlist exports.
- Circuit simulation, only when you ask for one, with the waveform graph in the chat.
- A design plan that later sessions start from.

## How the AI's work shows in the chat

As the AI works, the chat shows a row for each step, such as **Searching components**, **Placing components**, **Connecting components**, **Assigning power**, **Cleaning up wiring** and **Checking the design**. Related steps collapse into one summary row; click it to see the details.

A step that didn't work is shown in amber. That is usually not a failure of the whole request: the AI tries another way and keeps going.

## Related

- [AI assistant](ai-assistant.md)
- [Max mode](max-mode.md)
- [Component Lab](component-lab.md)
- [Design checks](design-checks.md)
