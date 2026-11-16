---
title: "AusTender contract awards API: OCDS findByDates example"
description: "How to pull Australian Government contract award notices from the AusTender OCDS API by publication date, what fields are included, and what is not."
---
# AusTender contract awards API

AusTender publishes Australian Government contract notices as OCDS JSON. The date-range endpoint needs no key.

## One request

```bash
curl -s "https://api.tenders.gov.au/ocds/findByDates/contractPublished/2026-11-13T00:00:00Z/2026-11-16T00:00:00Z"
```

You get a package of releases with `awards`, `contracts`, `parties` and `tender` blocks: contract value, UNSPSC code, contract period and the procuring agency.

## Things to know

- **Awards only.** This endpoint is for published contracts. Open Australian tenders are not offered for redistribution, so do not build a tender feed on it.
- **Supplier names** are not in the data this route returns.
- Publication dates in the query are ISO timestamps; keep ranges short and page through results politely.
- Check each contract on www.tenders.gov.au before relying on it. The materials are released by the Department of Finance under CC BY 3.0 AU.

## The ready-made route

The [EU & UK Public Tenders Monitor](https://apify.com/civic_data_feeds/public-tenders-monitor) on Apify includes AusTender awards as an optional source (`au-austender`) in the same flat schema as TED and the UK feeds. It costs $2.50 per 1,000 notices. See the [weekly sample](../public-tenders-monitor/index.md).
