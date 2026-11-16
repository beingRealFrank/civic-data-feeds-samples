---
title: "CanadaBuys tender notices as CSV or JSON: the open data files explained"
description: "Where the CanadaBuys open data tender files live, what the columns mean, how to read the multi-line and bilingual fields, and a ready-made JSON option."
---
# CanadaBuys tender notices as CSV or JSON

CanadaBuys, the Government of Canada's procurement site, publishes its tender notices as open data under the Open Government Licence - Canada. No login is needed.

## The files

Under `https://canadabuys.canada.ca/opendata/pub/` you will find:

- `openTenderNotice-ouvertAvisAppelOffres.csv`: notices that are open for bids now.
- `newTenderNotice-nouvelAvisAppelOffres.csv`: notices published recently.
- `<year>-<year+1>-TenderNotice-AvisAppelOffres.csv`: a whole fiscal year, open and closed (the federal fiscal year starts in April).

## Reading them

- Columns exist in English and French (`...-eng` and `...-fra`). Pick one language.
- **Several values in one cell:** the procurement category (goods, services, construction) can hold more than one value separated by line breaks, so split before you filter.
- **Descriptions contain HTML entities** such as `&eacute;`; decode them.
- **Amendments** are separate rows with an amendment number, so count notices by reference number, not by row.
- **Contact columns** hold named people, e-mails and phone numbers. If you republish data, decide whether you need them at all.

## The ready-made route

The [CanadaBuys Tenders Monitor](https://apify.com/civic_data_feeds/canadabuys-tenders-monitor) Actor on Apify turns the files into clean JSON: categories split, entities decoded, contact details left out, filters for keyword, province, category and UNSPSC prefix, and an only-new option for daily alerts. It costs $2.50 per 1,000 notices.

See a [live weekly sample](../canadabuys-tenders-monitor/index.md) with a CSV download.

Data source: CanadaBuys open data, Government of Canada, Open Government Licence - Canada.
