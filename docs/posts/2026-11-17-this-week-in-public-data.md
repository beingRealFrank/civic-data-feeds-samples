---
title: "This week in public data: 884 IT tenders in the EU, 64 GW of planned US batteries"
description: "A short data note from official sources: EU IT tender counts by country, a quiet week for new US grants, Canadian federal tenders by category, and where the US battery pipeline is."
---
# This week in public data (17 November 2026)

Four numbers from official public sources, each counted the same way you can repeat yourself.

## EU IT services tenders: 884 open competitions in a week

On TED, 884 contract notices in CPV division 72 (IT services) were published between 9 and 16 November 2026 (notice types `cn-standard`, `cn-social` and `cn-desg`). By buyer country:

| Country | Notices |
|---|---|
| Germany | 127 |
| Poland | 125 |
| Spain | 75 |
| France | 57 |
| Netherlands | 42 |
| Italy | 26 |

Poland publishing almost as many IT notices as Germany is the number to notice. How to run the same count: [the TED API guide](../guides/ted-tenders-api-csv.html) and [notice types explained](../guides/ted-notice-types-explained.html).

## US federal grants: a quiet week

Only 10 new opportunities were posted on Grants.gov in the last 7 days (status posted), against 19 in the previous 14-day window of our weekly sample. If you watch for new grants, a daily alert matters more in weeks like this because there is little noise. See the [Grants.gov search guide](../guides/grants-gov-api-search.html).

## Canada: 21 new federal tender notices

CanadaBuys' new-notice file lists 21 notices: 11 goods, 5 services, 3 construction and 2 services related to goods. The [CanadaBuys open data guide](../guides/canadabuys-tenders-open-data.html) explains the files.

## US power: 64 GW of planned batteries

The September 2026 EIA-860M workbook (released in October) lists 483 planned battery generator rows with 64.2 GW of nameplate capacity. Texas has 25.3 GW, California 9.9 GW, Arizona 6.6 GW, Oregon 2.9 GW and Nevada 2.9 GW. Row counts overstate projects, because one plant is often several rows. See [planned battery storage by state](../guides/planned-battery-storage-projects-by-state.html).

## Get the data yourself

I publish four Apify Actors that return these sources as clean JSON or CSV: [EU & UK Public Tenders](https://apify.com/civic_data_feeds/public-tenders-monitor), [US Federal Grants](https://apify.com/civic_data_feeds/us-grants-monitor), [CanadaBuys Tenders](https://apify.com/civic_data_feeds/canadabuys-tenders-monitor) and [US Power Plant Pipeline](https://apify.com/civic_data_feeds/us-power-plant-pipeline). The [weekly sample pages](../index.html) show a free slice of each.

Sources: TED (© European Union), Grants.gov (US public domain), CanadaBuys (Open Government Licence - Canada), EIA Form EIA-860M (US public domain). — Frank Gilroy
