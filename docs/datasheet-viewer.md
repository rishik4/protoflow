# Datasheet viewer

ProtoFlow opens component datasheets in its own PDF viewer, in a tab next to your schematic and board. It finds the datasheet for a part for you, and you can attach datasheets to the AI chat so the AI reads them directly.

## Open a part's datasheet

Any of these finds and opens the datasheet for a part:

- **Schematic:** select one part, right-click it and choose **View PDF Data Sheet**.
- **Properties panel:** select a part on the schematic or a footprint on the board and click **Open Datasheet** at the top of its properties.
- **Command palette:** select a part, press <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> and run **View Selected Component Data Sheet**.
- **Part picker:** while browsing parts, click **Open Datasheet** (or **Find Datasheet** when the part has no direct link) on the part's details.

ProtoFlow uses the part's own datasheet link first. If there is none, it looks up the manufacturer's datasheet, and only falls back to the catalog's PDF last, so you usually get the manufacturer's English PDF. If no PDF can be found, a message says so.

Datasheets load even from manufacturer sites that block direct downloads.

### Set a part's datasheet link

To point a part at a specific datasheet, select it and type the link into the **Datasheet** row in the Properties panel. The link is shared by every unit of a multi-unit part. Then click **Open Datasheet**.

In the [Symbol editor](symbol-editor.md), the **Datasheet** field in Properties sets the link for that symbol.

### Open a PDF from your computer

- Drag a `.pdf` file onto the ProtoFlow window, or
- Run **Open PDF Datasheet...** from the command palette and pick the file.

## Use the viewer

Each datasheet opens as its own tab, named after the file. Opening the same datasheet again switches to its existing tab. The tab remembers its page and zoom while you switch between tabs.

Opened datasheets are also listed under **Datasheets** in the **Project Explorer** panel, so you can get back to them. Right-click an entry and choose **Remove from Project Explorer** to clear it from the list.

The toolbar at the top of the viewer has:

| Control | What it does |
|---|---|
| **Search** | Find text in the PDF |
| **Bookmarks & Outline** | The PDF's table of contents, when it has one |
| **First page**, **Previous page**, **Next page**, **Last page** | Move through the pages |
| Page counter | Click it to jump to a page number |
| **Zoom out**, **Zoom in**, **Fit to width** | Change the zoom, from 25% to 500% |
| **More actions** | **Save to Downloads**, **Open in Browser**, **Copy Link** |

You can also zoom with a trackpad pinch or by double-clicking.

Select text in the PDF to get a **Translate** button, which translates the selection to English. This helps with datasheets that are only partly in English.

If a datasheet fails to load, the viewer offers **Retry** and **Open in Browser**.

### Shortcuts in the viewer

| Action | macOS | Windows/Linux |
|---|---|---|
| Search the PDF | <kbd>Cmd</kbd>+<kbd>F</kbd> | <kbd>Ctrl</kbd>+<kbd>F</kbd> |
| Next match | <kbd>Enter</kbd> | <kbd>Enter</kbd> |
| Previous match | <kbd>Shift</kbd>+<kbd>Enter</kbd> | <kbd>Shift</kbd>+<kbd>Enter</kbd> |
| Close search | <kbd>Esc</kbd> | <kbd>Esc</kbd> |
| Zoom in | <kbd>Cmd</kbd>+<kbd>=</kbd> | <kbd>Ctrl</kbd>+<kbd>=</kbd> |
| Zoom out | <kbd>Cmd</kbd>+<kbd>-</kbd> | <kbd>Ctrl</kbd>+<kbd>-</kbd> |
| Reset zoom | <kbd>Cmd</kbd>+<kbd>0</kbd> | <kbd>Ctrl</kbd>+<kbd>0</kbd> |

## Part details next to the datasheet

With a datasheet tab active, the Properties panel shows the part it belongs to: its LCSC number, manufacturer, part number, package, price and description, plus a **Preview** of its symbol, footprint and 3D model. Click **Place Component** to put the part on your schematic.

## Datasheets and the AI

- **Attach a datasheet.** Click **+** in the AI chat (tooltip **Attach image or PDF (or Ctrl+V to paste)**) or drag a PDF onto the AI panel. The AI reads the PDF's text directly to answer your question. For long datasheets it searches the pages it needs. Scanned PDFs with no text layer can't be read. File uploads in the AI chat need a paid plan.
- **Ask the AI to find one.** For example: "Find the datasheet for the ATmega328P and tell me the maximum clock speed." The AI looks the datasheet up and reads it.
- **Ask the AI to open one.** "Open the datasheet for U3" opens it in a viewer tab.
- **Links in AI replies.** Click a datasheet link in an AI reply to open it in the viewer.

The AI does not read a datasheet just because its tab is open. Attach it, or ask the AI to look it up.

## Related

- [Components and parts](components-and-parts.md)
- [AI assistant](ai-assistant.md)
- [Component Lab](component-lab.md)
