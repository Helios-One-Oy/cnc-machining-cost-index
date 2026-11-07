# QuotedPart CNC Machining Cost Index

Open data from [QuotedPart](https://quotedpart.com), the autonomous AI quoting software for CNC machining, sheet metal and job shops (made by Helios One Oy, Espoo, Finland).

This repository mirrors two CSV files published on quotedpart.com, byte for byte as the site serves them:

| File | What it is | Page (method, charts, notes) |
|---|---|---|
| [`data/cnc-cost-index-2026-11.csv`](data/cnc-cost-index-2026-11.csv) | CNC Machining Cost Index, November 2026 edition. 184 rows: 26 basket parts plus 2 reference parts re-priced in each of 10 materials, each at qty 1, 10, 100 and 1,000. | https://quotedpart.com/cnc-machining-cost-index |
| [`data/best-cnc-quoting-software-2026-11-06.csv`](data/best-cnc-quoting-software-2026-11-06.csv) | CNC quoting software comparison, November 6, 2026. 14 tools, one row each, with every price as the vendor stated it, source URLs and checked dates. | https://quotedpart.com/best-cnc-quoting-software |

Original download URLs:
- https://quotedpart.com/data/cnc-cost-index-2026-11.csv
- https://quotedpart.com/data/best-cnc-quoting-software-2026-11-06.csv

If this copy and the site ever differ, the site is the source.

## CNC Machining Cost Index

**What it is.** Each part is described the way a drawing would describe it: size, stock form, holes, pockets, turned diameters, bends, tolerance and finish. QuotedPart's pricing engine, the same one that prices a shop's quotes in the app, turns that into a routing with programming, setup and run minutes per operation, buys the stock, adds outside finishes and applies markup, at 1, 10, 100 and 1,000 pieces. The route for each part is fixed (the `process` column).

**What it is not.** These are not quotes collected from shops, not an average of what shops charge and not a market survey. They are what one documented set of default US rates and material prices produces (30% markup on cost, $65.00 minimum per quote line; machine rates, setup minutes and material prices are listed in the [methodology](https://quotedpart.com/cnc-machining-cost-index#methodology)). A shop with different rates, machines or markup will price the same parts differently. Please describe the figures as **engine estimates at stated default rates**.

**Editions.** The index is recomputed monthly on the catalog's current rates and material prices. The basket and its part IDs stay the same, so a change between editions is a change in inputs or in the engine, never in the parts. This is the November 2026 edition; material prices were checked October 21, 2026.

**Parts.** 3-axis milling M01-M12, 5-axis milling F01-F02, CNC turning T01-T06, Swiss turning S01-S02, laser cut sheet L01-L04 (`table` = `basket`); reference parts RM and RT re-priced in each material (`table` = `material`).

### Columns

| Column | Meaning |
|---|---|
| `edition` | Index edition, YYYY-MM |
| `table` | `basket` (the fixed parts) or `material` (a reference part re-priced in each material) |
| `part_id` | Stable part id; the same id is the same part in every edition |
| `part_name` | Part name |
| `process` | Routing the part is priced on |
| `material` | Material grade |
| `material_usd_per_lb` | Catalog small-lot stock price, USD per lb |
| `envelope` | Finished size, inches |
| `features` | Machined features |
| `tolerance` | General tolerance class |
| `finish` | Outside finish, if any |
| `qty` | Order quantity |
| `unit_price_usd` | Quoted price per part, USD, after markup and the line minimum |
| `lot_price_usd` | Quoted price for the whole lot, USD |
| `cost_per_part_usd` | Shop cost per part before markup, USD |
| `setup_share_pct` | Setup and programming, percent of cost |
| `run_share_pct` | Machine and labor run time, percent of cost |
| `material_share_pct` | Stock material, percent of cost |
| `outside_share_pct` | Outside finishes, percent of cost |
| `setup_min_per_lot` | Setup and programming minutes per lot |
| `run_min_per_part` | Run minutes per part before quantity learning |
| `lead_days` | Estimated lead time, working days |

Column definitions are copied from the "CSV columns" list on the index page.

## CNC quoting software comparison

The buyer's guide's comparison table as data: for each tool, what it is best for, the verdict, starting price and every price as the vendor's own pricing page stated it, trial, STEP / PDF / RFQ email input, AI autonomy, ERP links and ITAR wording, with the source URLs and the dates the facts and prices were checked. Facts about other tools come from their own websites, with the link and the date.

Disclosure: QuotedPart wrote this comparison and is one of the tools in it. The method is on the [guide page](https://quotedpart.com/best-cnc-quoting-software). Something wrong or out of date? Email support@quotedpart.com.

## License

Both files are licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/), as stated on quotedpart.com. You may share and adapt them for any purpose, with credit.

## How to cite

> QuotedPart CNC Machining Cost Index, November 2026, quotedpart.com/cnc-machining-cost-index

> QuotedPart, "Best CNC quoting software (2026): 12 tools compared", November 6, 2026, quotedpart.com/best-cnc-quoting-software

Machine-readable citation: [`CITATION.cff`](CITATION.cff).

## About QuotedPart

QuotedPart reads RFQ emails, STEP models and PDF drawings and prices every quantity from the shop's own rates. It has a public API and a remote MCP server at `https://quotedpart.com/mcp` ([docs](https://quotedpart.com/docs/mcp)). Facts with sources: https://quotedpart.com/facts and https://quotedpart.com/llms.txt.
