---
title: "TED notice types explained: cn-standard, can-standard and the rest"
description: "Which TED notice type codes are open competitions and which are contract awards, and how to use them in a TED Search API query."
---
# TED notice types explained

The TED Search API filters on `notice-type`. For most tender work you want one of two groups.

## Open competitions (you can still bid)

`cn-standard`, `cn-social`, `cn-desg` (contract notices), `pin-cfc-standard` and `pin-cfc-social` (prior information notices used as a call for competition), `qu-sy` (qualification system) and `subco` (subcontracting).

## Contract awards (who won)

`can-standard`, `can-social`, `can-desg` (contract award notices), `can-tran`, `veat` (voluntary ex ante transparency) and `can-modif` (modification).

## In a query

```bash
curl -s -X POST https://api.ted.europa.eu/v3/notices/search \
  -H 'content-type: application/json' \
  -d '{"query":"publication-date>=20261110 AND notice-type IN (can-standard can-social) AND buyer-country IN (DEU)","fields":["publication-number","notice-title","buyer-name"],"page":1,"limit":50}'
```

Use a space, not a comma, between values inside `IN (...)`. For the rest of the query syntax see the [TED API guide](ted-tenders-api-csv.md).

## The ready-made route

The [EU & UK Public Tenders Monitor](https://apify.com/civic_data_feeds/public-tenders-monitor) on Apify hides these codes behind one setting: **open competitions**, **contract awards**, or both, and adds the UK's Find a Tender and Contracts Finder in the same schema. It costs $2.50 per 1,000 notices. See the [weekly sample](../public-tenders-monitor/index.md).

Data source: TED, © European Union.
