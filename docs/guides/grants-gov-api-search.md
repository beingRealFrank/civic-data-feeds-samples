---
title: "Search Grants.gov programmatically: search2 and fetchOpportunity examples"
description: "How to search federal grant opportunities on Grants.gov without an API key, filter by agency and date, fetch award ceilings, and avoid the agency-code and date-window gotchas."
---
# Search Grants.gov programmatically

Grants.gov exposes a public search endpoint that needs no login or key. Two calls cover most uses.

## 1. Search

```bash
curl -s -X POST https://api.grants.gov/v1/api/search2 \
  -H 'content-type: application/json' \
  -d '{"rows":25,"keyword":"solar","oppStatuses":"forecasted|posted","dateRange":"14"}'
```

Gotchas that cost time:

- **Agencies** are matched exactly. `NSF` works, but a parent code like `HHS`, `DOE` or `USDA` returns zero hits until you add a wildcard: `HHS*`. A child code such as `HHS-NIH11` also works.
- **Statuses** are joined with `|`: `forecasted|posted`.
- **`dateRange`** only accepts fixed windows (3, 7, 14 and so on up to 56 days). Ask for the smallest window that covers you, then filter the exact dates yourself.
- **Search hits are thin.** They have the title, number, agency and open and close dates, but not the award ceiling or eligibility.

## 2. Fetch the details

Call `fetchOpportunity` with the opportunity id from a hit to get the award ceiling and floor, total funding, expected number of awards, eligible applicant types, cost sharing and the description. That is one extra request per opportunity, so keep to about one a second.

## The ready-made route

The [US Federal Grants Monitor](https://apify.com/civic_data_feeds/us-grants-monitor) on Apify does both calls, handles the agency wildcard and date windows, redacts personal contact details from free text, and can return only opportunities you have not seen before on a schedule. It costs $2.50 per 1,000 opportunities.

See a [live weekly sample](../us-grants-monitor/index.md) with a CSV download.

Data source: Grants.gov, a US federal government website (public domain).
