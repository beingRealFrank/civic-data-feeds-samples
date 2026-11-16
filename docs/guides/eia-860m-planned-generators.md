---
title: "EIA-860M planned power plants: download, status codes and how to filter"
description: "Where to get the monthly EIA-860M generator inventory, what the status codes mean, and how to filter planned solar, wind and battery projects by state and capacity."
---
# EIA-860M: planned US power plants

The EIA's Form EIA-860M is a monthly spreadsheet of US generators of 1 MW or more: operating, planned, retired, and canceled or postponed. The planned sheet is the closest public view of the new-build pipeline.

## Get the file

EIA publishes each month's workbook under `https://www.eia.gov/electricity/data/eia860m/`. The file name follows the pattern `xls/<month>_generator<year>.xlsx` (for example `september_generator2026.xlsx`). The workbook has separate sheets for Operating, Planned, Canceled or Postponed and Retired.

## Status codes on planned units

| Code | Meaning |
|---|---|
| P | Planned, regulatory approvals not started |
| L | Regulatory approvals pending |
| T | Regulatory approvals received |
| U | Under construction, less than half complete |
| V | Under construction, more than half complete |
| TS | Construction complete, testing, not yet in commercial operation |

## Things to watch

- Capacity figures in 860M are preliminary and are sometimes revised later; the annual EIA-860 is the reliable record.
- A project's planned operating month moves often. Compare month to month to catch slips, not just new entries.
- Technology names are free text from filers (`Solar Photovoltaic`, `Batteries`, `Onshore Wind Turbine`), so normalize before you group.

## The ready-made route

The [US Power Plant Pipeline](https://apify.com/civic_data_feeds/us-power-plant-pipeline) Actor on Apify reads the workbook for you and returns one tidy row per generator with owner, plant, state, county, coordinates, balancing authority, technology, MW, status and planned online month. Filter by state, technology, minimum MW and status, and turn on the new-or-changed option to get only what moved since your last run. It costs $4 per 1,000 generators.

See a [live sample of planned Texas solar and battery projects](../us-power-plant-pipeline/index.md) with a CSV download.

Data source: U.S. Energy Information Administration, Form EIA-860M (public domain).
