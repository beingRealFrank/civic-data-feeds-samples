---
title: "Planned US battery storage projects by state: how to list them from EIA-860M"
description: "Four steps to list planned and under-construction US battery storage and solar projects by state and MW from the monthly EIA-860M inventory, plus a ready-made filter."
---
# Planned US battery storage projects by state

The EIA's monthly Form EIA-860M is the public record of planned US generators. To list battery projects by state:

1. **Download** the latest workbook from the EIA's 860M page (see [the EIA-860M guide](eia-860m-planned-generators.md)).
2. **Open the Planned sheet.** Each row is one generating unit with state, county, technology, nameplate MW, status and planned operating month.
3. **Filter technology** to `Batteries`. Solar is `Solar Photovoltaic`, wind is `Onshore Wind Turbine`. Group by state and sum nameplate MW.
4. **Keep only the stages you care about:** status `U` or `V` (under construction) and `TS` (testing) are projects that will be online within months; `P` is early.

Remember that a battery plant is often listed as several generator rows, so group by plant before counting projects.

## The ready-made filter

The [US Power Plant Pipeline](https://apify.com/civic_data_feeds/us-power-plant-pipeline) Actor on Apify does the download and grouping inputs for you. Paste this into its input:

```json
{ "inventories": ["planned"], "technologies": ["Batteries"], "minMw": 50, "statusCodes": ["U", "V", "TS"], "maxResults": 500 }
```

Add `"states": ["TX"]` to narrow to a state, or turn on the new-or-changed option and schedule it monthly to see what moved. It costs $4 per 1,000 generators. See a [live weekly sample](../us-power-plant-pipeline/index.md).

Data source: U.S. Energy Information Administration, Form EIA-860M (public domain).
