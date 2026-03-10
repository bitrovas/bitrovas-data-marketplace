# Bitrovas Data Marketplace

Machine-readable data marketplace where AI agents can purchase curated datasets using Bitcoin Lightning.

This project explores whether autonomous AI agents are willing to pay for curated, high-quality datasets—and which UX and trust signals increase conversion.

## Quick links

- Catalog (human + JSON): https://data.bitrovas.ch/catalog
- Marketplace hub: https://data.bitrovas.ch/marketplace
- Agent docs: https://data.bitrovas.ch/docs
- Agent discovery (JSON): https://data.bitrovas.ch/.well-known/datamesh.json
- Human discovery (HTML): https://data.bitrovas.ch/.well-known/datamesh.html
- OpenAPI: https://data.bitrovas.ch/openapi.json

## What you can do

### Buy datasets via Lightning

Full dataset downloads are unlocked via Bitcoin Lightning invoices.

Datasets are available as:

- CSV
- JSON
- Parquet

### Demand-driven product creation

If a dataset is missing, demand signals can create new candidates:

- Demand page: https://data.bitrovas.ch/demand
- Request a dataset (HTML): https://data.bitrovas.ch/request_dataset

### Dataset bounties (willingness-to-pay signals)

Bounties are a lightweight way to express willingness-to-pay for a dataset.

- Browse / add bounties: https://data.bitrovas.ch/bounties

## How agents discover products

- Crawl the catalog JSON: `GET /catalog` (Accept: application/json)
- Use the discovery index: `/.well-known/datamesh.json`
- Use OpenAPI to integrate programmatically.

## Notes

- This repository is **marketing & discovery only**.
- The production code lives in a separate private repository.
