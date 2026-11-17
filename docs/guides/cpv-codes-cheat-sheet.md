---
title: "CPV codes cheat sheet: the main divisions of EU public procurement"
description: "The two-digit CPV divisions used in EU tenders (45 construction, 48 software, 72 IT services, 71 engineering and more), and how to filter TED notices by CPV prefix."
---
# CPV codes cheat sheet

The Common Procurement Vocabulary (CPV) classifies what an EU tender buys. The first two digits are the **division**; more digits narrow it down (an 8-digit code is the most specific). Filter on a prefix to cover a whole sector.

| Division | Covers |
|---|---|
| 03 | Agricultural, farming, fishing and forestry products |
| 09 | Petroleum products, fuel, electricity |
| 15 | Food, beverages, tobacco |
| 22 | Printed matter |
| 30 | Office and computing machinery, equipment and supplies |
| 31 | Electrical machinery, apparatus, equipment |
| 32 | Radio, television, communication equipment |
| 33 | Medical equipment, pharmaceuticals, personal care |
| 34 | Transport equipment |
| 35 | Security, fire-fighting, police and defence equipment |
| 39 | Furniture, domestic appliances |
| 42 | Industrial machinery |
| 44 | Construction structures and materials |
| 45 | Construction work |
| 48 | Software package and information systems |
| 50 | Repair and maintenance services |
| 55 | Hotel, restaurant and retail services |
| 60 | Transport services |
| 64 | Postal and telecommunications services |
| 65 | Public utilities |
| 66 | Financial and insurance services |
| 70 | Real estate services |
| 71 | Architectural, construction, engineering and inspection services |
| 72 | IT services: consulting, software development, Internet and support |
| 73 | Research and development services |
| 75 | Administration, defence and social security services |
| 79 | Business services: law, marketing, consulting, recruitment, printing, security |
| 80 | Education and training services |
| 85 | Health and social work services |
| 90 | Sewage, refuse, cleaning and environmental services |
| 92 | Recreational, cultural and sporting services |
| 98 | Other community, social and personal services |

## Filtering on TED

In a TED Search API query, `classification-cpv=72*` matches every code starting with 72, and `classification-cpv=48*` matches software packages. Combine prefixes with `OR`: `(classification-cpv=72* OR classification-cpv=48*)`. A full 8-digit code is matched exactly. See the [TED API guide](ted-tenders-api-csv.md) for a working request and [notice types](ted-notice-types-explained.md).

## Ready-made

The [EU & UK Public Tenders Monitor](https://apify.com/civic_data_feeds/public-tenders-monitor) takes CPV prefixes directly (`"cpvCodes": ["72", "48"]`) and returns TED, Find a Tender and Contracts Finder notices in one schema. See the [weekly sample](../public-tenders-monitor/index.md).

Source: CPV is defined in Regulation (EC) No 213/2008; TED data © European Union.
