# Crossborder Product Radar

Crossborder Product Radar is a private, local-first research tool for cross-border e-commerce product and keyword analysis.

It helps screen long-tail product ideas by combining keyword demand, marketplace supply, domestic sourcing cost estimates, risk filters, and manual validation data.

This project is an internal research assistant. It is not an advertising automation tool, marketplace listing tool, or automated purchasing system.

---

## Purpose

The goal of this project is to reduce manual product research workload.

The tool is designed to help answer questions such as:

* Are people searching for this product keyword?
* Is there existing marketplace supply?
* Are current listings weak, overpriced, or poorly optimized?
* Is there potential domestic sourcing advantage?
* Is the product lightweight, low-risk, and suitable for manual validation?

The tool does not guarantee profitability.

---

## What It Does

The project may support:

* Long-tail product keyword generation.
* Keyword demand research.
* Marketplace active listing analysis.
* Domestic sourcing cost estimation.
* Risk filtering.
* Opportunity scoring.
* Local research report generation.
* Manual eBay Product Research validation import.

---

## What It Does Not Do

This tool does not:

* Create, modify, or manage Google Ads campaigns.
* Create or manage Google Ads accounts.
* Change bids, budgets, ads, or ad groups.
* Perform conversion tracking or remarketing.
* Automatically create eBay listings.
* Automatically place orders.
* Automatically process payments.
* Scrape logged-in eBay Seller Hub / Terapeak pages.
* Bypass platform access controls, captchas, or rate limits.

All final business decisions require manual review.

---

## Google Ads API Usage

Google Ads API access, if configured, is used only for Keyword Planning Services, such as:

* Keyword ideas.
* Historical keyword metrics.
* Average monthly searches.
* Competition level.
* Bid range estimates.

The tool does not support any Google Ads campaign types.

---

## eBay Usage

The tool may use eBay public APIs to inspect current active marketplace supply.

eBay Product Research / Terapeak validation is manual. The tool generates candidates for review, and the user manually records Product Research metrics before making sourcing decisions.

---

## Basic Workflow

```bash
python scripts/run_daily.py --mock --market EBAY_US --geo US --limit 100
```

Expected outputs may include:

```text
data/reports/latest/daily_report.md
data/reports/latest/top_candidates.csv
data/reports/latest/manual_research_queue.csv
```

Manual validation data can be imported later:

```bash
python scripts/import_manual_product_research.py --file data/manual/product_research.csv
```

---

## Environment Variables

Create a local `.env` file. Do not commit real credentials.

See `.env.example` for required variables.

Common variables include:

```env
EBAY_CLIENT_ID=
EBAY_CLIENT_SECRET=

SERPAPI_API_KEY=

APIFY_TOKEN=

CJ_API_KEY=

GOOGLE_ADS_DEVELOPER_TOKEN=
GOOGLE_ADS_CLIENT_ID=
GOOGLE_ADS_CLIENT_SECRET=
GOOGLE_ADS_REFRESH_TOKEN=
GOOGLE_ADS_LOGIN_CUSTOMER_ID=
GOOGLE_ADS_CUSTOMER_ID=
```

---

## Security

Never commit API keys, OAuth secrets, refresh tokens, account IDs, cookies, or private credentials.

Recommended `.gitignore` entries:

```gitignore
.env
*.env
client_secret.json
google-ads.yaml
*.sqlite
*.db
data/raw/
data/private/
```

If a credential is exposed, rotate or reset it immediately.

---

## Status

This project is an early-stage internal research framework.

It is designed to run locally and support mock data mode while external API integrations are being configured.

---

## Disclaimer

This tool provides research assistance only.

Marketplace data, keyword metrics, sourcing costs, shipping costs, and platform policies may change. A high opportunity score does not mean a product will sell profitably.

The user is responsible for manual validation, sourcing decisions, platform compliance, product safety checks, tax, customs, and legal considerations.
