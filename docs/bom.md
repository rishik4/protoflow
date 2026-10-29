# BOM

The bill of materials (BOM) lists every part in your schematic with its quantity, catalog part number and price. ProtoFlow builds it from the schematic as you work, so there is nothing to generate by hand.

## Open the BOM

Use any of these:

- Click **BOM** in the view switcher at the top of the window. This opens the BOM in its own tab, linked to the schematic.
- Click the **Bill of Materials** button in the schematic toolbar.
- Search for **Bill of Materials** in the command palette (<kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>). The palette can also open it as a side panel.

The full-screen view has a **Dock to side panel** button, and the side panel has **Switch to full screen**.

## What the BOM shows

| Column | Contents |
|---|---|
| **REFERENCE** | Reference designators, such as R1, R2, R5 |
| **VALUE** | The part value, such as 10k or 100nF |
| **QTY** | How many of this part the board uses |
| **CATALOG** | The LCSC part number (C-number), or the part number from the distributor you chose |
| **UNIT PRICE** | Price per part |
| **LINE TOTAL** | Quantity times unit price |

Click a column header to sort by it. Drag the dividers to resize columns.

**GROUPED** (the default) puts identical parts on one row. **INDIVIDUAL** shows one row per part. Power and ground symbols, and parts marked to be left out of the BOM, are not listed.

The top of the BOM counts unique parts, total parts and how many are priced. The footer shows the total cost. It turns green when every row has a price; otherwise a warning says some parts are missing prices.

Hover over a row and click **Highlight on schematic** to find that part in the schematic.

## Prices

### Automatic prices

Every part with an LCSC part number gets its price looked up automatically, at the price break for the quantity the BOM needs.

For parts with no price and no part number, click **FIND PRICES**. ProtoFlow searches the catalog by manufacturer part number, or by value, and fills in the part number and price it finds.

### Compare distributors

Click a row to expand it. The **DISTRIBUTOR PRICING** section shows the price, the price at your quantity, and the stock at LCSC, DigiKey and Mouser. The lowest in-stock price is marked **BEST**. Click **USE** to source the part from that distributor. You need to be signed in for these lookups.

The expanded row also has links to the **Datasheet** and the **LCSC page**, and a button to copy the part number.

### Enter a price yourself

Click the **UNIT PRICE** cell of any row to type a price. A price you type wins over the catalog price. Clear the cell to go back to the catalog price. Typed prices are kept while ProtoFlow is open, but they are not saved with the design.

### BOM Insights

On a paid plan, **ANALYZE** grades the BOM on cost and supply risk. It shows the board cost, the cost per board at 10 and 100 boards, how many parts are in stock, and how many are at risk. Each expanded row then shows stock, a risk level and the price breaks. See [pricing](https://www.protoflow.ai/pricing) for plans.

## Swap or find parts

Expand a row to see:

- **Swap part** (or **Find part** when the row has no catalog number): opens the component search with the part number, or the value, already filled in. Choose a new part there.
- **Find cheaper part** and **Find alternatives**: open the AI assistant with a prompt for that part. The AI suggests options and asks before it changes anything.

**FIND CHEAPER** in the footer asks the AI to look for savings across the whole BOM.

While the BOM tab is active, the AI panel works as the BOM Agent. Its quick actions include **Audit BOM**, **Find Cheaper**, **Cheapest Distributor**, **Export CSVs** and **Fix Metadata**. See [AI assistant](ai-assistant.md).

## Export

Click **EXPORT CSV** in the footer. The export dialog has two sections:

- **BY DISTRIBUTOR**: one CSV per distributor, with that distributor's part number, the MPN and manufacturer. Parts with no part number go in an "Unassigned" file.
- **COMBINED**: one CSV with every part. You can also copy it to the clipboard.

**SAVE ALL TO FOLDER** writes every file at once. Files are named after the schematic, for example `MyBoard_BOM_All.csv` and `MyBoard_BOM_LCSC.csv`.

The combined CSV has the columns Reference, Value, Quantity, Catalog Part, Distributor, Unit Price and Line Total, followed by a total row.

For an assembly BOM in a board house's format, export from the PCB editor instead. See [Manufacturing](manufacturing.md).

## Related

- [Components and parts](components-and-parts.md)
- [Manufacturing](manufacturing.md)
- [AI assistant](ai-assistant.md)
