---
title: "UNSPSC codes on CanadaBuys: the segments that matter for tenders"
description: "How UNSPSC product and service codes appear on Canadian federal tender notices, the main two-digit segments, and how to filter CanadaBuys notices by UNSPSC prefix."
---
# UNSPSC codes on CanadaBuys tenders

CanadaBuys notices carry a `unspsc` column (and a `gsin` column for the older Government Services Identification Number). UNSPSC is an eight-digit code; the first two digits are the **segment**. Many notices leave the column empty, so do not rely on it alone.

## Main segments

| Segment | Covers |
|---|---|
| 10-15 | Live plants and animals, food, raw materials |
| 20-27 | Mining, industrial machinery, tools |
| 30-32 | Building and construction materials, components, electronics |
| 39-41 | Electrical equipment, lab and measuring equipment |
| 42 | Medical equipment and supplies |
| 43 | Information technology, broadcasting and telecommunications |
| 44-45 | Office equipment, printing and photographic equipment |
| 46 | Defence, law enforcement and safety equipment |
| 47-49 | Cleaning equipment, sports and recreation |
| 50-52 | Food and beverage products, furniture, appliances |
| 56 | Furniture and furnishings |
| 70-73 | Farming, fishing, forestry and building construction and maintenance services |
| 76 | Industrial cleaning services |
| 77-78 | Environmental services, transportation and storage |
| 80 | Management and business professional services |
| 81 | Engineering, research and technology services |
| 82-84 | Editorial, design, public utilities, finance |
| 85 | Healthcare services |
| 86 | Education and training services |
| 90-95 | Travel, food service, personal services, public order, land and buildings |

## Filtering

In the CSV, keep rows whose `unspsc` starts with your segment (`43`, `81`). The category column (goods, services, construction) is a coarser filter that is filled in more consistently. See [the CanadaBuys open data guide](canadabuys-tenders-open-data.md).

The [CanadaBuys Tenders Monitor](https://apify.com/civic_data_feeds/canadabuys-tenders-monitor) takes `"unspsc": ["43", "81"]` prefixes and category filters directly. See the [weekly sample](../canadabuys-tenders-monitor/index.md).

Data source: CanadaBuys open data, Government of Canada, Open Government Licence - Canada.
