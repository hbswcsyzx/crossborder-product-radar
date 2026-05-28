# Crossborder Product Radar

Crossborder Product Radar is a private, local-first product and keyword research tool for cross-border e-commerce research.

The tool is designed to help identify product-related keyword opportunities by combining keyword demand data, marketplace supply data, estimated domestic sourcing costs, and manual validation results.

This project is not an advertising automation tool. It does not create, modify, or manage Google Ads campaigns.

---

## Purpose

The purpose of this tool is to support internal product research.

It helps answer questions such as:

* Are people searching for this type of product?
* Is there existing marketplace supply?
* Are current listings weak, overpriced, or poorly optimized?
* Is there potential domestic sourcing advantage?
* Is the product low-risk, lightweight, and suitable for manual validation?
* Which candidates are worth checking manually in eBay Product Research?

The tool is intended to reduce manual research workload by filtering a large number of product keywords into a smaller list of candidates for human review.

It does not guarantee profitability.

---

## Current Status

This project is an early-stage internal research framework.

The current goal is to generate local research reports and manual validation queues.

It is not a production SaaS application, not a public service, and not an automated selling system.

---

## Intended Users

This tool is intended for internal use only.

Intended users:

* The project owner.
* Direct technical assistants or contractors working under the project owner's supervision.

This tool is not designed for public users, external clients, advertisers, agencies, or third-party account management.

---

## What This Tool Does

The tool may perform the following research tasks:

* Generate long-tail product keyword candidates.
* Filter out high-risk or unsuitable product categories.
* Retrieve keyword research metrics where authorized.
* Retrieve current marketplace supply data.
* Estimate pricing, shipping, sourcing cost, and margin.
* Generate product opportunity scores.
* Produce daily local reports.
* Produce a manual eBay Product Research validation queue.
* Import manually verified eBay Product Research results.
* Re-score product candidates after manual validation.

---

## Google Ads API Usage

This tool uses Google Ads API only for keyword research and keyword demand analysis.

Planned Google Ads API usage:

* Keyword Planning Services.
* Keyword idea generation.
* Historical keyword metrics.
* Average monthly searches.
* Competition level and competition index.
* Low and high top-of-page bid range estimates.

The tool does not support any Google Ads campaign types.

Specifically, it does not support:

* Search campaigns.
* Performance Max campaigns.
* Display campaigns.
* Shopping campaigns.
* Video campaigns.
* App campaigns.
* Demand Gen campaigns.

The tool does not create, modify, or manage:

* Google Ads accounts.
* Campaigns.
* Ad groups.
* Ads.
* Keywords inside ad accounts.
* Bids.
* Budgets.
* Conversion tracking.
* Remarketing audiences.
* App conversion tracking.
* Reporting dashboards for ad performance.

Google Ads API access is used only to retrieve keyword planning data from accounts that the project owner owns or has explicitly authorized.

---

## eBay Usage

This tool may use eBay public APIs, such as eBay Browse API, to inspect current active marketplace supply.

Possible eBay research data includes:

* Active listing samples.
* Product titles.
* Price ranges.
* Shipping cost estimates.
* Item location.
* Seller information exposed by the public API.
* Marketplace URLs.

This tool does not automatically access, scrape, or bypass eBay Seller Hub Product Research / Terapeak pages.

eBay Product Research validation is intentionally manual.

The expected workflow is:

1. The tool generates product candidates.
2. The user manually checks selected candidates in eBay Product Research.
3. The user records Product Research metrics in a local CSV file.
4. The tool imports the manual data and recalculates scores.

This tool does not automatically list products on eBay.

---

## What This Tool Does Not Do

This tool does not:

* Automatically create Google Ads campaigns.
* Automatically manage Google Ads accounts.
* Automatically create or edit ads.
* Automatically change bids or budgets.
* Automatically perform remarketing.
* Automatically create eBay listings.
* Automatically place orders.
* Automatically process payments.
* Automatically contact suppliers.
* Automatically purchase inventory.
* Automatically scrape logged-in eBay Seller Hub pages.
* Bypass captchas, rate limits, login restrictions, or platform access controls.
* Guarantee product profitability.
* Provide legal, tax, customs, or compliance advice.

All final business decisions must be made manually by the user.

---

## Data Sources

Depending on local configuration, the tool may use some of the following data sources:

* Google Ads API Keyword Planning Services.
* eBay Browse API.
* SerpApi.
* Apify Actors.
* CJdropshipping API.
* Domestic sourcing CSV files manually prepared by the user.
* Manually entered eBay Product Research data.

Not every data source is required.

The project is designed to support mock data mode so the framework can run without all API credentials.

---

## Manual Validation Requirement

Automated data is only used for initial screening.

Before sourcing or testing any product, the user should manually validate:

* eBay Product Research total sold.
* eBay Product Research average sold price.
* eBay Product Research sell-through rate.
* eBay Product Research total sellers.
* Recent sold dates.
* Active listing quality.
* Domestic supply quality.
* Shipping feasibility.
* Platform policy risk.
* Product safety and compliance risk.

A product candidate should not be treated as validated until manual Product Research and sourcing checks are completed.

---

## Risk Filtering

The tool is designed to reject or heavily penalize high-risk categories.

Examples of categories that should be filtered out:

* Food.
* Supplements.
* Medicine.
* Cosmetics.
* Skincare.
* Medical devices.
* Children's toys.
* Baby products.
* Batteries.
* Power banks.
* Chargers.
* Plug-in electronics.
* Heated devices.
* Weapons.
* Knives.
* Tactical goods.
* Firearms or firearm accessories.
* Counterfeit goods.
* Replica branded goods.
* Unauthorized IP merchandise.
* Adult products.
* Gambling-related goods.
* CBD, THC, or controlled substances.

Low-risk product types are preferred, such as:

* Storage accessories.
* Craft supplies.
* Non-electric desktop accessories.
* Blank materials.
* Organizers.
* Dust covers.
* Labels.
* Small non-safety replacement parts.
* Lightweight hobby accessories.

Risk filtering is only a preliminary software filter. The user remains responsible for final compliance checks.

---

## Scoring Philosophy

The tool does not simply search for popular products.

The goal is to identify long-tail opportunities where:

* There is measurable search demand.
* There is some existing marketplace buying activity.
* Current supply is limited, weak, overpriced, or poorly presented.
* Domestic sourcing may provide cost or variety advantages.
* Product risk is low.
* Shipping is feasible.
* Estimated margin is sufficient.
* The product is suitable for manual verification.

The tool distinguishes between:

* Real opportunities.
* Markets that are too small.
* Red-ocean markets.
* Information-only search terms.
* Low-margin products.
* High-risk products.

---

## Example Workflow

### 1. Run daily research

```bash
python scripts/run_daily.py --market EBAY_US --geo US --limit 100
```

### 2. Review generated reports

Expected outputs:

```text
data/reports/latest/daily_report.md
data/reports/latest/top_candidates.csv
data/reports/latest/manual_research_queue.csv
```

### 3. Manually check eBay Product Research

For selected candidates, manually record:

* Total sold.
* Average sold price.
* Sold price range.
* Average shipping.
* Sell-through rate.
* Total sellers.
* Date last sold.
* Notes.

### 4. Import manual validation data

```bash
python scripts/import_manual_product_research.py --file data/manual/product_research.csv
```

### 5. Export validated candidates

```bash
python scripts/export_candidates.py --status ready_to_source
```

---

## Environment Variables

Create a local `.env` file.

Do not commit `.env` to source control.

Example:

```env
EBAY_CLIENT_ID=
EBAY_CLIENT_SECRET=

SERPAPI_API_KEY=

APIFY_TOKEN=
APIFY_EBAY_SOLD_ACTOR_ID=

CJ_API_KEY=
CJ_ACCESS_TOKEN=

GOOGLE_ADS_DEVELOPER_TOKEN=
GOOGLE_ADS_CLIENT_ID=
GOOGLE_ADS_CLIENT_SECRET=
GOOGLE_ADS_REFRESH_TOKEN=
GOOGLE_ADS_LOGIN_CUSTOMER_ID=
GOOGLE_ADS_CUSTOMER_ID=

TARGET_MARKETS=US
PRICE_MIN_USD=15
PRICE_MAX_USD=80
MIN_MARGIN_PCT=30
MAX_WEIGHT_G=500
```

---

## Credential Security

Never commit credentials to this repository.

Sensitive credentials include:

* Google Ads developer token.
* Google OAuth client ID.
* Google OAuth client secret.
* Google Ads refresh token.
* eBay client ID.
* eBay client secret.
* SerpApi key.
* Apify token.
* CJdropshipping API key.
* Any access token or refresh token.

The `.env` file should be listed in `.gitignore`.

Recommended `.gitignore` entries:

```gitignore
.env
*.env
client_secret.json
google-ads.yaml
data/raw/
data/private/
*.sqlite
*.db
```

If any credential is accidentally exposed publicly, rotate or reset it immediately.

---

## Local-First Design

The first version of this project is designed to run locally.

It stores research data in a local database and generates local reports.

The project does not expose a public web service by default.

If a dashboard is added in the future, it should remain private unless additional security, access control, and compliance review are completed.

---

## Mock Mode

The framework should support mock mode for local development.

Example:

```bash
python scripts/run_daily.py --mock --market EBAY_US --geo US --limit 100
```

Mock mode allows development and testing without external API credentials.

---

## Limitations

This tool has several important limitations:

* Google Ads keyword data is an estimate, not exact demand.
* Marketplace API data may not represent complete market supply.
* Third-party scraper data may be incomplete or inaccurate.
* eBay Product Research data must be manually verified.
* Domestic sourcing cost estimates may change.
* Shipping cost and delivery time may change.
* Platform policies may change.
* A high opportunity score does not mean a product will sell profitably.

The tool is a research assistant, not an automatic decision-maker.

---

## Compliance Position

This project is designed to be a compliant internal research tool.

It uses Google Ads API only for Keyword Planning Services and keyword demand analysis.

It does not automate advertising, campaign management, bidding, account management, remarketing, or conversion tracking.

It does not automate marketplace listing, purchasing, or payment.

It does not scrape logged-in Seller Hub / Terapeak pages.

It does not guarantee business outcomes.

---

## Repository Notice

This repository may contain source code, configuration templates, and mock data.

It must not contain:

* Real API keys.
* Real OAuth secrets.
* Real refresh tokens.
* Private account identifiers.
* Customer data.
* Payment data.
* Supplier private agreements.
* Non-public marketplace data.

---

## License

This project is currently intended for private/internal research use.

A public open-source license has not yet been selected.

Do not reuse this project for external commercial services without reviewing applicable API terms, marketplace policies, data provider terms, and compliance requirements.

---

## Contact

Project owner: DaiVernon Research Tools

For compliance or API-related questions, contact the API contact email configured in the relevant developer console.
