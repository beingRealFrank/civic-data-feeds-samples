---
title: "Find a Tender vs Contracts Finder: which UK procurement notices are where"
description: "The difference between the UK's Find a Tender and Contracts Finder services, which contracts appear on each, how their APIs filter dates, and how to search both."
---
# Find a Tender vs Contracts Finder

The UK has two official public procurement notice services, and a contract can be on one, the other, or both.

| | Find a Tender | Contracts Finder |
|---|---|---|
| Covers | Higher-value, above-threshold procurement | Lower-value contracts in England (from about £12,000, or £30,000 for central government) |
| API date filter | `updatedFrom` / `updatedTo` (last update time) | `publishedFrom` / `publishedTo` (publication date) |
| Format | OCDS release packages | OCDS releases |
| Notice page | `find-tender.service.gov.uk/Notice/<id>` | `contractsfinder.service.gov.uk/Notice/<id>` |

## What this means in practice

- **To find every UK opportunity in a sector, search both.** Above-threshold work is on Find a Tender; the long tail of smaller contracts is on Contracts Finder.
- **A notice can show up twice** on Find a Tender because the date filter is the *update* time. Deduplicate by notice id.
- **Scotland, Wales and Northern Ireland** have their own portals for devolved procurement, so some contracts appear on neither service.

Working API requests for each are in the [Find a Tender guide](find-a-tender-ocds-api.md) and the [Contracts Finder guide](uk-contracts-finder-api.md).

## Searching both at once

The [EU & UK Public Tenders Monitor](https://apify.com/civic_data_feeds/public-tenders-monitor) on Apify queries both UK services and the EU's TED in one flat schema, with an only-new option for scheduled runs. It costs $2.50 per 1,000 notices. See the [weekly sample](../public-tenders-monitor/index.md).

Contains public sector information licensed under the Open Government Licence v3.0.
