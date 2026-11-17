---
title: "Grants.gov forecasted vs posted opportunities: what each status means"
description: "How forecasted, posted, closed and archived opportunities differ on Grants.gov, which dates a forecast has, and how to get ahead of grants before they open."
---
# Grants.gov forecasted vs posted opportunities

Grants.gov lists each federal funding opportunity in one of four states, and you can search them with the `oppStatuses` parameter.

| Status | Meaning |
|---|---|
| forecasted | Announced in advance; the application has not opened yet |
| posted | Open: the full notice and application package are available |
| closed | The application deadline has passed |
| archived | Older, finished opportunities kept for reference |

## Why forecasts matter

A **forecasted** opportunity gives you weeks or months of lead time. Instead of an exact deadline, it carries estimated dates: estimated post date, estimated close date and estimated award date, plus a fiscal year. Those are plans and can move, so treat them as a heads-up and check the notice when it is posted.

## Searching

```bash
curl -s -X POST https://api.grants.gov/v1/api/search2 \
  -H 'content-type: application/json' \
  -d '{"rows":25,"oppStatuses":"forecasted","keyword":"energy"}'
```

Join statuses with `|` to search both: `"oppStatuses":"forecasted|posted"`. More search tips (agency wildcards, date windows) are in the [Grants.gov API guide](grants-gov-api-search.md), and the [code tables](grants-gov-applicant-type-codes.md) cover applicant types.

## Ready-made

The [US Federal Grants Monitor](https://apify.com/civic_data_feeds/us-grants-monitor) on Apify returns forecasted and posted opportunities in one schema, with the estimated dates filled in for forecasts, award ceilings, eligibility and an only-new option for daily alerts. It costs $2.50 per 1,000 opportunities. See the [weekly sample](../us-grants-monitor/index.md).

Data source: Grants.gov, a US federal government website (public domain).
