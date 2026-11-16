---
title: "UK Contracts Finder API: search notices as OCDS JSON, with paging example"
description: "How to query the free Contracts Finder OCDS search endpoint for UK public contract notices by publication date, how paging works, and what the JSON contains."
---
# UK Contracts Finder API: notices as OCDS JSON

Contracts Finder lists lower-value UK public contracts (from about £12,000, or £30,000 for central government) and publishes them as Open Contracting Data Standard (OCDS) JSON. No key is needed.

## One request

```bash
curl -s "https://www.contractsfinder.service.gov.uk/Published/Notices/OCDS/Search?publishedFrom=2026-11-15&limit=100"
```

The response has a `releases` array and a `links.next` URL. Follow `links.next` until it is absent; it carries a cursor, so do not build page numbers yourself.

## What a release contains

- `tender`: title, description, value, tender period (the deadline), classification (CPV codes) and procurement method.
- `buyer` and `parties`: organisation names and addresses.
- `awards`: present on award notices, with the supplier and value.
- `tag`: tells you whether the release is a tender, an award or an update.

## Things to watch

- Filtering is by publication date only. Keyword and value filtering is up to you, on records you have fetched, so long date ranges take several pages.
- Release ids look like `<notice-guid>-<release number>`, and one notice can have several releases, so deduplicate on the guid.
- Be polite: about one request a second, and wait when the service asks you to slow down.

## The ready-made route

The [EU & UK Public Tenders Monitor](https://apify.com/civic_data_feeds/public-tenders-monitor) on Apify reads Contracts Finder, Find a Tender and the EU's TED in one flat schema, with keyword, country, CPV and value filters and an only-new option for scheduled runs. It costs $2.50 per 1,000 notices.

See a [live weekly sample](../public-tenders-monitor/index.md) with a CSV download. Related: [the Find a Tender API](find-a-tender-ocds-api.md).

Contains public sector information licensed under the Open Government Licence v3.0.
