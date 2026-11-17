---
title: "TED publication numbers and notice links: how to build a URL to any EU tender notice"
description: "How TED publication numbers like 786291-2026 work, how to turn them into notice page and XML links, and what the Search API returns for links."
---
# TED publication numbers and notice links

Every notice on TED has a **publication number** in the form `<serial>-<year>`, for example `786291-2026`. It is the one identifier you need.

## Build the links

- **Notice page (English):** `https://ted.europa.eu/en/notice/-/detail/786291-2026`
- **XML:** `https://ted.europa.eu/en/notice/786291-2026/xml`
- **PDF:** `https://ted.europa.eu/en/notice/786291-2026/pdf` (the language segment changes, for example `/de/`)

The Search API also returns a `links` object per notice with ready-made `xml` and `pdf` URLs keyed by language, so you can ask for the `publication-number` field and build the rest yourself.

## Using it as a key

- Use the publication number as your primary key when you store notices. A new version of a notice gets its own publication number rather than overwriting the old one, so keep both.
- The year in the number is the year of publication, which is not always the year of the procedure.
- Titles and buyer names are returned as objects keyed by language, so store the language you picked with them.

For a working search request see the [TED API guide](ted-tenders-api-csv.md), and for the notice type codes see [notice types explained](ted-notice-types-explained.md).

## Ready-made

The [EU & UK Public Tenders Monitor](https://apify.com/civic_data_feeds/public-tenders-monitor) returns each notice with its official `url`, a stable `id` (`ted:<publication number>`) and flat fields for buyer, CPV codes, deadline and value. See the [weekly sample](../public-tenders-monitor/index.md).

Data source: TED, © European Union.
