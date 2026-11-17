---
title: "EIA-860M canceled, postponed and retired generators: what the sheets contain"
description: "What the Canceled or Postponed and Retired sheets in the EIA-860M workbook hold, with row counts and MW by technology from the September 2026 workbook, and how to use them."
---
# EIA-860M canceled, postponed and retired generators

Besides the Planned and Operating sheets, the monthly EIA-860M workbook has two sheets that are useful for pipeline analysis: **Canceled or Postponed** and **Retired**.

## What is in the September 2026 workbook

| Sheet | Rows | Nameplate MW | Largest technologies (MW) |
|---|---|---|---|
| Canceled or Postponed | 1,745 | 185,357 | Natural gas combined cycle 59,466; gas combustion turbine 31,064; solar PV 29,246; onshore wind 15,752; batteries 15,441; conventional steam coal 15,409 |
| Retired | 7,321 | 297,740 | Conventional steam coal 145,939; gas steam turbine 67,294; petroleum liquids 26,669; gas combustion turbine 20,813; gas combined cycle 14,054; nuclear 8,980 |

These are totals of every row in each sheet as published, not a single month's changes. The Retired sheet adds operating and retirement month and year columns, so you can slice it by date; the Canceled sheet has no date column.

## How to use them

- **Attrition rate:** compare canceled or postponed capacity with planned capacity by technology to see which project types tend to drop out.
- **Retirement wave:** filter the Retired sheet on retirement year, and group by technology and state to see where coal capacity has gone.
- **Replace and repower sites:** retired plants with grid connections are candidates for new storage or solar; join on plant id with the Planned sheet.

Remember that a plant is often several generator rows, so group by plant id before counting plants. Column meanings are in the [technology and energy source codes guide](eia-860m-technology-energy-source-codes.md) and [status codes](eia-860m-planned-generators.md).

## Ready-made

The [US Power Plant Pipeline](https://apify.com/civic_data_feeds/us-power-plant-pipeline) Actor reads all four inventories: `"inventories": ["planned", "canceled", "operating", "retired"]`. Filter by state, technology and minimum MW, and turn on the new-or-changed option for a monthly watch. It costs $4 per 1,000 generators. See the [weekly sample](../us-power-plant-pipeline/index.md).

Data source: U.S. Energy Information Administration, Form EIA-860M (public domain). Figures computed from the September 2026 workbook.
