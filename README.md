# Wheelhouse Underwriting Tool

Revenue projection tool powered by the Wheelhouse CompSet API.

## Quick Start

```bash
# 1. Install dependencies
pip install -r requirements.txt

# 2. Set up your API keys
cp .env.example .env
# Edit .env with your real keys (already pre-filled with current keys)

# 3. Run
python server.py

# 4. Open http://localhost:8000
```

## Architecture

```
server.py      → Flask proxy (solves CORS) + serves the frontend
index.html     → React SPA (search, map, table, projection)
openapi.json   → Wheelhouse CompSet API spec
.env           → API keys (git-ignored)
```

## API Endpoints (proxied)

| Local Route | Wheelhouse API |
|---|---|
| `GET /api/candidates?lat=&long=&radius=&limit=` | `/candidates` |
| `GET /api/candidates/listing/<id>` | `/candidates/listing/<id>` |
| `GET /api/candidates/listings?listing_ids=` | `/candidates/listings` |
| `GET /api/geocode?q=<address>` | Nominatim geocoder |

## Features

- **Search**: By address, lat/long, or listing ID
- **Map**: Leaflet map with comp markers, search radius, subject property pin
- **Widgets**: Toggle visible columns (matching Wheelhouse UI)
- **Filters**: Bedrooms, bathrooms, room types sidebar
- **Projection**: Revenue projections with adjustable assumptions
- **Pro Forma**: NOI, cash flow, cap rate, cash-on-cash return
