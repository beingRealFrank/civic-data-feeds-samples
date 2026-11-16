---
title: "Find a Tender API: UK above-threshold notices as OCDS JSON"
description: "How to read the Find a Tender (UK) OCDS release packages API: the updatedFrom parameter, cursor paging, and how it differs from Contracts Finder."
---
# Find a Tender API: UK notices as OCDS JSON

Find a Tender is the UK service for higher-value procurement. It publishes release packages in OCDS format and needs no key.

## One request

```bash
curl -s "https://www.find-tender.service.gov.uk/api/1.0/ocdsReleasePackages?updatedFrom=2026-11-15T00:00:00&limit=100"
```

Each release has `buyer`, `parties`, `tender` and `tag`. The response includes `links.next` with a cursor. Keep following it until it is empty.

## How it differs from Contracts Finder

- The filter is `updatedFrom` (and `updatedTo`), the time a notice was last updated, not the first publication date. A notice can therefore appear again after an update.
- It covers above-threshold procurement; lower-value contracts in England are on [Contracts Finder](uk-contracts-finder-api.md).
- Notice pages are at `https://www.find-tender.service.gov.uk/Notice/<id>`.

## The ready-made route

The [EU & UK Public Tenders Monitor](https://apify.com/civic_data_feeds/public-tenders-monitor) on Apify returns Find a Tender, Contracts Finder and TED notices in one flat schema and can return only notices you have not seen before. It costs $2.50 per 1,000 notices. See the [weekly sample](../public-tenders-monitor/index.md).

Contains public sector information licensed under the Open Government Licence v3.0.
