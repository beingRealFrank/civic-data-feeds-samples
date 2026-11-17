---
title: "TED notice pages return HTTP 202 with an empty body: what it is and what to do"
description: "Why ted.europa.eu notice XML, PDF and HTML links can return 202 with x-amzn-waf-action: challenge, how that differs from the Search API, and how to get notice data reliably."
---
# TED notice pages return HTTP 202 with an empty body

If a script downloads TED notice pages (the `/xml`, `/pdf`, `/html` or `/detail` links) and gets **HTTP 202, an empty body and a `x-amzn-waf-action: challenge` header**, the request was stopped by a web application firewall challenge, not by a missing notice. The status looks like success, so code that only checks for a 2xx will happily save an empty file.

## What I saw (17 November 2026)

From one machine with plain `curl`, all four of these returned `202`, `text/html`, 0 bytes and the challenge header:

- `https://ted.europa.eu/en/notice/756345-2026/xml`
- `https://ted.europa.eu/en/notice/756345-2026/pdf`
- `https://ted.europa.eu/en/notice/756345-2026/html`
- `https://ted.europa.eu/en/notice/-/detail/756345-2026`

In the same minute, six consecutive calls to the Search API (`POST https://api.ted.europa.eu/v3/notices/search`) all returned `200`. Other people have reported the same notice links working from other networks, so the behaviour is intermittent and depends on where and how you call.

## What to do

1. **Treat 202 with the challenge header as a failure**, not as data. Check the body length and the content type (`application/xml` or `application/pdf`), and never accept an empty or HTML body as XML or PDF.
2. **Prefer the Search API** for notice data. Ask for the fields you need (`publication-number`, `notice-title`, `buyer-name`, `deadline-receipt-tender-date-lot`, `classification-cpv` and more) instead of downloading and parsing each notice page. See the [TED API guide](ted-tenders-api-csv.md) and [publication numbers and links](ted-notice-links-and-publication-numbers.md).
3. **If you must fetch a notice document,** space requests out (about one a second), retry a challenged URL later with backoff, and keep a record of which URLs were challenged so a run does not report partial success as complete.
4. **Send links, not copies,** when you only need a human to open the notice: the `https://ted.europa.eu/en/notice/-/detail/<publication-number>` page opens fine in a normal browser.

## Ready-made

The [EU & UK Public Tenders Monitor](https://apify.com/civic_data_feeds/public-tenders-monitor) reads notices through the Search API, so it is not affected by the page challenge, and it returns the official notice link in the `url` field. See the [weekly sample](../public-tenders-monitor/index.md).

Data source: TED, © European Union.
