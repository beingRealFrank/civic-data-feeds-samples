---
title: "EIA-860M technology names, energy source codes and prime movers (with planned capacity)"
description: "What the Technology, Energy Source Code and Prime Mover columns contain in the EIA-860M planned generators sheet, with row counts and MW from the September 2026 workbook."
---
# EIA-860M technology names, energy source codes and prime movers

Three columns describe what a planned generator is: **Technology** (free-text label), **Energy Source Code** and **Prime Mover Code**. Here are the combinations in the Planned sheet of the September 2026 workbook (released October 2026), ranked by nameplate capacity.

| Technology | Energy source | Prime mover | Rows | Nameplate MW |
|---|---|---|---|---|
| Solar Photovoltaic | SUN | PV | 1,100 | 122,025 |
| Batteries | MWH | BA | 483 | 64,235 |
| Natural Gas Fired Combustion Turbine | NG | GT | 192 | 22,995 |
| Natural Gas Fired Combined Cycle | NG | CT | 144 | 22,629 |
| Onshore Wind Turbine | WND | WT | 73 | 18,454 |
| Natural Gas Fired Combined Cycle | NG | CA | 75 | 14,328 |
| Natural Gas Fired Combined Cycle | NG | CS | 14 | 8,631 |
| Offshore Wind Turbine | WND | WS | 4 | 5,089 |
| Nuclear | NUC | ST | 5 | 4,968 |
| Hydroelectric Pumped Storage | WAT | PS | 11 | 2,600 |
| Natural Gas Internal Combustion Engine | NG | IC | 66 | 952 |
| Conventional Hydroelectric | WAT | HY | 117 | 431 |

## How to read it

- **A combined-cycle plant is several rows** (combustion turbines `CT` plus steam `CA` or `CS`), so add them up per plant before counting plants or you will double count.
- **Technology is the label to group by**; energy source and prime mover are the codes to join to other EIA data.
- Planned capacity is nameplate and preliminary; much of it never gets built, so check the status code (see [status codes](eia-860m-planned-generators.md)) before treating a row as a firm project.

## Filtering

In the [US Power Plant Pipeline](https://apify.com/civic_data_feeds/us-power-plant-pipeline) Actor you can filter on the technology label (`"technologies": ["Natural Gas Fired Combined Cycle"]`) or the energy source (`"energySources": ["NG"]`). See the [weekly sample](../us-power-plant-pipeline/index.md) and the [battery storage by state guide](planned-battery-storage-projects-by-state.md).

Data source: U.S. Energy Information Administration, Form EIA-860M (public domain). Figures computed from the Planned sheet of the September 2026 workbook.
