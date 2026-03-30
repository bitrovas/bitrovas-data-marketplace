# Bitrovas Data Marketplace

Machine-readable data marketplace and agent-commerce reference system where AI agents can discover, evaluate, pay for, and consume datasets and services using Bitcoin Lightning.

This public repository is the lightweight discovery/marketing mirror for the Bitrovas ecosystem. The production implementation lives elsewhere, but the canonical public entry points are stable and machine-readable.

## Site structure

- `https://bitrovas.ch` → top-level ecosystem root
- `https://data.bitrovas.ch` → marketplace, catalog, docs, and handshake entry points
- `https://clawrence.bitrovas.ch` → Clawrence experiment/blog/service layer

## Quick links

### Core ecosystem
- Root: https://bitrovas.ch
- Root sitemap: https://bitrovas.ch/sitemap.xml
- Root robots: https://bitrovas.ch/robots.txt
- Bitrovas Handshake Protocol v0.2: https://bitrovas.ch/handshake-protocol-v0-2.html
- Ecosystem handshake JSON: https://bitrovas.ch/.well-known/bitrovas.json

### Marketplace
- Marketplace: https://data.bitrovas.ch/marketplace
- Catalog: https://data.bitrovas.ch/catalog
- Docs: https://data.bitrovas.ch/docs
- Handshake docs: https://data.bitrovas.ch/docs/handshake
- Agent quickstart: https://data.bitrovas.ch/agent-quickstart
- Auth docs: https://data.bitrovas.ch/docs/auth
- Rate limits: https://data.bitrovas.ch/docs/rate-limits
- Terms: https://data.bitrovas.ch/terms
- Marketplace handshake JSON: https://data.bitrovas.ch/.well-known/bitrovas.json
- OpenAPI: https://data.bitrovas.ch/openapi.json

### Clawrence
- Clawrence root: https://clawrence.bitrovas.ch
- What is Clawrence: https://clawrence.bitrovas.ch/what-is-clawrence
- AI Agent Economy: https://clawrence.bitrovas.ch/ai-agent-economy
- Lightning Data Services: https://clawrence.bitrovas.ch/lightning-data-services
- Experiments overview: https://clawrence.bitrovas.ch/experiments-overview
- Clawrence insights: https://clawrence.bitrovas.ch/insights
- Clawrence handshake JSON: https://clawrence.bitrovas.ch/.well-known/bitrovas.json
- Clawrence agent.json: https://clawrence.bitrovas.ch/agent.json

### Root-only actions
- Donate: https://bitrovas.ch/donate
- Feedback / contact: https://bitrovas.ch

## Bitrovas Handshake Protocol v0.2

Bitrovas exposes a public handshake standard so external AI agents do not need custom glue code for every page or service.

### Handshake phases
1. **Discovery**
2. **Capability description**
3. **Trust / ratings**
4. **Pricing**
5. **Payment**
6. **Fulfillment**
7. **Error handling**

### Canonical rule
Every AI agent should start with one of these machine-readable entry points:

```bash
curl https://bitrovas.ch/.well-known/bitrovas.json
curl https://data.bitrovas.ch/.well-known/bitrovas.json
curl https://clawrence.bitrovas.ch/.well-known/bitrovas.json
```

## Two service families under one standard

### 1) Marketplace / data products
The marketplace uses the handshake for:
- catalog discovery
- product manifests
- trust signals
- ratings discovery
- invoice creation
- payment status polling
- download fulfillment

Typical flow:

```bash
curl https://data.bitrovas.ch/.well-known/bitrovas.json
curl -H 'Accept: application/json' https://data.bitrovas.ch/catalog
curl https://data.bitrovas.ch/catalog/world_countries_codes/2026-03-09/trust
curl https://data.bitrovas.ch/catalog/world_countries_codes/2026-03-09/ratings
curl -X POST https://data.bitrovas.ch/invoice \
  -H 'Content-Type: application/json' \
  -d '{"dataset":"world_countries_codes","version":"2026-03-09","format":"json"}'
curl 'https://data.bitrovas.ch/payment_status?payment_hash=PAYMENT_HASH'
curl -L 'https://data.bitrovas.ch/download?payment_hash=PAYMENT_HASH&format=json' -o dataset.json
```

### 2) Clawrence / agent services
Clawrence uses the same handshake logic for preview-first, Lightning-unlocked services.

Typical flow:

```bash
curl https://clawrence.bitrovas.ch/.well-known/bitrovas.json
curl -X POST https://clawrence.bitrovas.ch/api/quality/preview \
  -H 'Content-Type: application/json' \
  -d '{"csv_text":"name,email\nAlice,alice@example.com"}'
curl -X POST https://clawrence.bitrovas.ch/api/quality/invoice \
  -H 'Content-Type: application/json' \
  -d '{"purpose":"quality_full_report","amount_sats":100}'
curl 'https://clawrence.bitrovas.ch/api/quality/status?payment_hash=PAYMENT_HASH'
curl -X POST https://clawrence.bitrovas.ch/api/quality/run \
  -H 'Content-Type: application/json' \
  -d '{"payment_hash":"PAYMENT_HASH","csv_text":"name,email\nAlice,alice@example.com"}'
```

## Repository purpose

This public repository is used for discovery and marketing only.

It contains public machine-readable or human-readable artifacts such as:
- `datasets.json`
- `agent.json`
- `datasets/*.md`

The production marketplace and Clawrence implementation remain outside this public mirror and are not fully reproduced here.
