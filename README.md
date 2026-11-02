# B2B Data Extraction, Threat Intel & Lead Automation Workflows (Apify + n8n + Python/Node.js)

Production-ready **n8n automation workflows**, **Python/Node.js starter pipelines**, and **OpenAPI 3.0 specifications** powered by lightweight, schema-validated Apify Actors (`128 MB` zero-overhead runtime).

---

## Live Apify Store Actors

| Actor | Apify Store URL | Primary Use Case |
| :--- | :--- | :--- |
| **Shopify Products, Inventory & Barcodes Scraper** | [`hoanle0126/shopify-store-product-scraper`](https://apify.com/hoanle0126/shopify-store-product-scraper) | Competitor price monitoring, SKU/barcode extraction, variant inventory tracking |
| **Apple App Store Reviews & Ratings Scraper** | [`hoanle0126/apple-app-store-reviews-scraper`](https://apify.com/hoanle0126/apple-app-store-reviews-scraper) | Mobile app sentiment analysis, version regression tracking, competitor review mining |
| **Reddit Posts, Comments & Buying-Intent Lead Scraper** | [`hoanle0126/reddit-lead-monitor-scraper`](https://apify.com/hoanle0126/reddit-lead-monitor-scraper) | B2B social listening, high-intent buyer lead generation, pain-point discovery |
| **US Census Address Geocoder, FIPS & Census Tract Scraper** | [`hoanle0126/us-census-geocoder-fips-tract-block-demographics-scraper`](https://apify.com/hoanle0126/us-census-geocoder-fips-tract-block-demographics-scraper) | Batch street address geocoding to 15-digit FIPS State/County/Tract/Block codes for FinTech/Real Estate |
| **FIRST.org EPSS CVE Exploit Probability & Threat Intel Scraper** | [`hoanle0126/first-epss-cve-exploit-probability-threat-intel-scraper`](https://apify.com/hoanle0126/first-epss-cve-exploit-probability-threat-intel-scraper) | Automated vulnerability prioritization with daily EPSS probability & percentile scores |

---

## Quickstart: Run via Apify REST API (cURL / Python / Node.js / n8n)

### 1. CVE EPSS Exploit Probability Enrichment (`hoanle0126/first-epss-cve-exploit-probability-threat-intel-scraper`)
```bash
curl -X POST "https://api.apify.com/v2/acts/hoanle0126~first-epss-cve-exploit-probability-threat-intel-scraper/run-sync-get-dataset-items?token=YOUR_APIFY_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "cves": ["CVE-2024-3094", "CVE-2023-44487", "CVE-2021-44228"],
    "maxItems": 50
  }'
```

### 2. US Census Address -> FIPS & Census Tract Geocoder (`hoanle0126/us-census-geocoder-fips-tract-block-demographics-scraper`)
```bash
curl -X POST "https://api.apify.com/v2/acts/hoanle0126~us-census-geocoder-fips-tract-block-demographics-scraper/run-sync-get-dataset-items?token=YOUR_APIFY_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "addresses": [
      "1600 Pennsylvania Ave NW, Washington, DC 20500",
      "350 Fifth Ave, New York, NY 10118"
    ]
  }'
```

### 3. Reddit Buying-Intent B2B Lead Monitor (`hoanle0126/reddit-lead-monitor-scraper`)
```bash
curl -X POST "https://api.apify.com/v2/acts/hoanle0126~reddit-lead-monitor-scraper/run-sync-get-dataset-items?token=YOUR_APIFY_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "queries": ["looking for CRM alternative", "recommend web scraping tool"],
    "sort": "new",
    "maxItems": 25
  }'
```

### 4. Shopify Store Catalog & Variant Pricing Monitor (`hoanle0126/shopify-store-product-scraper`)
```bash
curl -X POST "https://api.apify.com/v2/acts/hoanle0126~shopify-store-product-scraper/run-sync-get-dataset-items?token=YOUR_APIFY_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "storeUrls": ["https://allbirds.com"],
    "maxProductsPerStore": 50
  }'
```

---

## Ready-to-Import n8n Workflows (`./n8n-workflows/`)

- [`n8n-workflows/daily-cve-epss-security-alert.json`](./n8n-workflows/daily-cve-epss-security-alert.json) — Scheduled daily CVE EPSS exploit probability check via Apify (`hoanle0126~first-epss-cve-exploit-probability-threat-intel-scraper`).
- [`n8n-workflows/reddit-b2b-lead-monitor.json`](./n8n-workflows/reddit-b2b-lead-monitor.json) — Automated B2B buying-intent lead monitor on Reddit via Apify (`hoanle0126~reddit-lead-monitor-scraper`).
- [`openapi/b2b-intel-api.openapi.json`](./openapi/b2b-intel-api.openapi.json) — OpenAPI 3.0.3 specification for the edge B2B Cyber, Network, Compliance & Geo Intelligence API (`https://b2b-intel-api.hoanle0126.workers.dev`).
