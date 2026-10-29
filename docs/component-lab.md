# Component Lab

The AI Component Lab makes a linked symbol and footprint for a part. Give it a part name, a datasheet or a pinout image and the AI generates both halves. If you already have one half, it generates only the missing one. If you have both, it links them without using AI. You can save the result to your library or export it for another tool.

## Open the Component Lab

The lab opens in its own tab, titled **AI Component Lab**. There is one lab tab; opening it again brings the existing tab to the front.

- Click **+** at the end of the tab bar and choose **Component Generator**.
- Choose **File** > **New** > **AI Component Lab**.
- Open the command palette (<kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>) and run **New AI Component Lab**.
- In the **Components** panel, click the AI Component Lab button next to the search box. It shows for your library categories, not for **Online** search.
- On the welcome screen, open **New** and choose **Generate Component**.

You can also start from a part that is already placed. In the part's properties, **Generate with AI** under the package opens the lab and links the new footprint back to that part. When the AI chat offers to create a custom part, choose **Open in Component Lab**: once you save the part to your library, the chat places it for you.

A generation keeps running if you switch to another tab.

## Inputs

Fill in any combination of these. You can type into the fields, click **Browse**, or drag files onto the tab.

| Input | What it accepts |
|---|---|
| **Part name** | Free text, for example `LM358`, `ESP32-WROOM-32` or `NE555` |
| **Datasheet URL (optional)** | A link to the datasheet |
| **PDF / image** | A datasheet PDF, or a pinout image (PNG, JPG, JPEG, WebP or GIF) |
| **Symbol** | KiCad (`.kicad_sym`, `.lib`), Altium (`.SchDoc`), EAGLE (`.lbr`), EDIF (`.edn`, `.edif`) or EasyEDA Pro symbol files |
| **Footprint** | KiCad (`.kicad_mod`), Altium (`.PcbDoc`), EAGLE (`.lbr`) or EasyEDA Pro footprint files |
| **3D model** | STEP (`.step`, `.stp`), WRL or X3D |

An empty **Symbol** or **Footprint** slot also offers **Draw**, which opens the [Symbol editor](symbol-editor.md) or [Footprint editor](footprint-editor.md) so you can draw that half yourself.

## Generate a part

1. Enter a **Part name**, a datasheet URL, or attach a datasheet PDF or pinout image.
2. Optionally import a symbol or footprint you already have.
3. Pick a model from the **Generation model** menu. Each model shows its cost multiplier, such as **1×**. Some models need a paid plan.
4. Click the main button. Its label tells you what will happen:
   - **Generate**: the AI makes both the symbol and the footprint.
   - **Generate footprint** or **Generate symbol**: you imported one half, so the AI makes only the other.
   - **Link & Build**: you imported both halves. ProtoFlow links them with no AI and no usage.
5. Watch the progress log. It shows steps such as finding the datasheet, extracting its text, analyzing the pinout and package, checking the pad geometry against the datasheet drawing, and building the symbol and footprint.

The line under the button shows how many generations you have left today and this month. When the included generations run out, the lab shows the credit cost of a generation instead. AI generation needs you to be signed in to ProtoFlow; **Link & Build** does not.

## Review the result

The result shows the **Symbol** and **Footprint** previews side by side, with:

- A summary: part name, manufacturer, part number, pin and pad counts, and a description.
- A pin table with **Pad**, **Name**, **Type** and **Side** columns.
- Warnings, when the AI found something to check, such as a pinout that doesn't match the package.

Hover a preview and click **Edit symbol** or **Edit footprint** to open it in the [Symbol editor](symbol-editor.md) or [Footprint editor](footprint-editor.md). When you save there, the change goes back into the lab.

To add a 3D model after generating, drop a STEP, WRL or X3D file on the 3D bar. Use **Replace 3D model** or **Remove 3D model** to change it.

## Part details

Open **Part details** to add optional information: **Manufacturer**, **Manufacturer part number**, **Category**, **Description**, extra datasheets and where to buy the part. When the AI reads these from the datasheet, a card says how many details it filled in.

The same section has a sharing switch. Parts are **Private** by default and saved only to your local library. Switch to **Public** to share the part with the community parts library when you save it.

## Save or export

- **Save to Library** stores the linked symbol and footprint in your custom library, ready to place. The button changes to **Saved**.
- **Export** writes the part for another tool:

| Menu item | Files |
|---|---|
| **Export for KiCad** | `.kicad_sym` and a `.pretty` footprint folder |
| **Export for EAGLE** | One `.lbr` library |
| **Export for Altium** | `.SchDoc` and `.PcbDoc` |
| **Export for Allegro/OrCAD** | EDIF (`.edn`) and a KiCad footprint, with import notes |

An attached 3D model is included in every export and every save.

## Related

- [Components and parts](components-and-parts.md)
- [Symbol editor](symbol-editor.md)
- [Footprint editor](footprint-editor.md)
- [AI assistant](ai-assistant.md)
