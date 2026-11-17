---
title: "Grants.gov applicant type codes (eligibilities) and funding category codes"
description: "The Grants.gov search eligibility codes (00, 12, 23, 25 and more) and funding category codes, with a note on which code means nonprofits and which means Others."
---
# Grants.gov applicant type and funding category codes

The `search2` endpoint filters on `eligibilities` and `fundingCategories` with short codes. Several are easy to mix up.

## Applicant types (`eligibilities`)

| Code | Applicant type |
|---|---|
| 00 | State governments |
| 01 | County governments |
| 02 | City or township governments |
| 04 | Special district governments |
| 05 | Independent school districts |
| 06 | Public and state-controlled institutions of higher education |
| 07 | Native American tribal governments (federally recognized) |
| 08 | Public housing authorities / Indian housing authorities |
| 11 | Native American tribal organizations (other than federally recognized) |
| 12 | Nonprofits with 501(c)(3) status (other than higher education) |
| 13 | Nonprofits without 501(c)(3) status (other than higher education) |
| 20 | Private institutions of higher education |
| 21 | Individuals |
| 22 | For-profit organizations other than small businesses |
| 23 | Small businesses |
| 25 | Others (read the eligibility text) |
| 99 | Unrestricted |

Note that **12 is the code for 501(c)(3) nonprofits**. `25` means "Others", which is a catch-all and not a nonprofit filter. Join several codes with `|` in the request: `"eligibilities": "12|23"`.

## Funding categories (`fundingCategories`)

Common codes: `AG` Agriculture, `AR` Arts, `BC` Business and Commerce, `CD` Community Development, `ED` Education, `EN` Energy, `ENV` Environment, `HL` Health, `HO` Housing, `HU` Humanities, `NR` Natural Resources, `ST` Science and Technology, `T` Transportation, `O` Other.

## Using them

```bash
curl -s -X POST https://api.grants.gov/v1/api/search2 \
  -H 'content-type: application/json' \
  -d '{"rows":25,"oppStatuses":"posted","eligibilities":"12","fundingCategories":"ED","dateRange":"28"}'
```

The [US Federal Grants Monitor](https://apify.com/civic_data_feeds/us-grants-monitor) on Apify takes the same codes as dropdowns and returns award ceilings and eligibility text for each opportunity. See the [weekly sample](../us-grants-monitor/index.md) and the [Grants.gov API guide](grants-gov-api-search.md).

Data source: Grants.gov, a US federal government website (public domain).
