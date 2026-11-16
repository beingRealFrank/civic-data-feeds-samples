---
title: "Get EU tender notices from TED as JSON or CSV (free API and a ready-made option)"
description: "How to query the free TED Search API v3 for EU public tenders by CPV code, country and date, with a working curl example, plus an option that also adds UK notices."
---
# Get EU tender notices from TED as JSON or CSV

TED (Tenders Electronic Daily) publishes EU public procurement notices. Its Search API v3 is free and needs no key for published notices.

## The free route: one request

```bash
curl -s -X POST https://api.ted.europa.eu/v3/notices/search \
  -H 'content-type: application/json' \
  -d '{
    "query": "publication-date>=20261110 AND classification-cpv=72* AND notice-type IN (cn-standard)",
    "fields": ["publication-number","notice-title","buyer-name","buyer-country","publication-date"],
    "page": 1,
    "limit": 100
  }'
```

What to know before you build on it:

- **Dates** in the query are `YYYYMMDD`.
- **CPV codes** accept a trailing `*` for a prefix, so `72*` is all IT services.
- **Country** is a three-letter code: `buyer-country IN (DEU POL)`.
- **Notice types** matter. `cn-standard` is a normal contract notice (an open competition); award notices use types such as `can-standard`.
- **Titles and buyer names** come back as objects keyed by language (`eng`, `deu`, ...), so pick one language and fall back to English.
- **Values and deadlines are per lot**, so one notice can carry several of each.
- **Paging:** request `page` 2, 3, ... until you have everything. Keep to about one request a second.

## The ready-made route

If you would rather not write the paging, language handling and lot logic, the [EU & UK Public Tenders Monitor](https://apify.com/civic_data_feeds/public-tenders-monitor) on Apify returns one flat row per notice, adds the UK's Find a Tender and Contracts Finder in the same schema, and can return only notices you have not seen before on a schedule. It costs $2.50 per 1,000 notices.

See a [live weekly sample of new IT tenders](../public-tenders-monitor/index.md) with a CSV download.

Data source: TED, © European Union. Notices carry the source's attribution.
