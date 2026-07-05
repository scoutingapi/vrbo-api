<!-- generated: DO NOT EDIT BY HAND — produced by apps/web/scripts/export-github-repos.ts from content/platforms/vrbo-api.ts. Edit the config + re-run. -->

# Vrbo API — search, availability & price data in one schema (2026)

**[Get a free API key →](https://scoutingapi.com/signup)** — free tier, no credit card.

Vrbo has no self-serve public API — only gated channel-manager onboarding for property managers. ScoutingAPI gives you live Vrbo search, availability, and pricing in the same schema as Airbnb, Booking.com, and Google Hotels. Vrbo and Airbnb in one call.

This repository is a resource hub for the modern **Vrbo API**: REST endpoints, working code samples in six languages, and recipes you can copy in under five minutes. It is not a maintained SDK (the official typed client is [`@scoutingapi/sdk`](https://scoutingapi.com/docs/sdk)) — it is a curated set of examples and references that match the machine contract at [openapi.json](https://api.scoutingapi.com/openapi.json). Every response is the same unified schema across Airbnb, Booking.com, Vrbo and Google Hotels, so one integration covers them all.

`99.9% uptime SLA` · `Failed calls cost 0 credits` · `Native MCP for AI agents` · `One unified schema`

---

## Quick start

Search live Vrbo stays with one HTTPS call — a bearer token, no SDK, no partner approval.

```bash
curl -s "https://api.scoutingapi.com/v1/search" \
  -G --data-urlencode "location=Split, HR" \
  --data-urlencode "platforms=vrbo" \
  --data-urlencode "limit=5" \
  -H "Authorization: Bearer $SCOUTINGAPI_KEY" \
  | jq '.data[] | {platform, name, price}'
```

You get back the unified `{ "data": [...], "meta": {...} }` envelope. [Sign up](https://scoutingapi.com/signup) for a free key, set `SCOUTINGAPI_KEY`, and the request runs as-is. Prefer to try before signing up? A `scout_test_` sandbox key returns deterministic fixtures at **zero cost**.

---

## What you can pull

The Vrbo data surface maps to these REST endpoints — each one HTTPS call, returning the unified schema, billed only on success:

- **Search** — `GET /v1/search` — Cross-platform property discovery, merged into one schema.
- **Price** — `GET /v1/price` — A real price quote for one listing, for your dates and occupancy.
- **Price compare** — `GET /v1/price-compare` — Cross-OTA price comparison for one property — the flagship endpoint.
- **Availability** — `GET /v1/availability` — Day-by-day availability for a known listing over a date window.
- **Listing** — `GET /v1/listing/{platform}/{id}` — Full listing detail — amenities, photos, host, and optional live price.
- **Reviews** — `GET /v1/reviews` — Normalized, paginated reviews for one listing.
- **Account** — `GET /v1/account` — Check your plan, credit balance and rate limit — programmatically.

Full machine contract: [openapi.json](https://api.scoutingapi.com/openapi.json). Per-endpoint references: [`endpoints/`](endpoints/).

**Ready to try?** [Get a free ScoutingAPI key →](https://scoutingapi.com/signup).

---

## What you can build

- **STR investment & arbitrage underwriting** — Pull live Vrbo nightly rates and availability for a target market, combine with occupancy signals, and underwrite a deal in your own model — across Vrbo and Airbnb, not just one source.
- **Vrbo-vs-Airbnb competitive pricing** — Benchmark a listing’s nightly price against comparable Vrbo and Airbnb inventory for the same dates; feed a pricing engine that sees both closed platforms at once.
- **Portfolio & market benchmarking** — Track a portfolio’s Vrbo listings against the local competitive set — rating, amenities, price, availability — in one normalized feed.
- **Availability monitoring & price-drop alerts** — Poll /v1/availability for a Vrbo property and date range; fire a Slack, email, or Telegram alert on a change or a price drop — shippable from /workflows in minutes.
- **Multi-platform availability checks** — The executive-retreat agency that “stopped checking availability by hand across four platforms” now makes one call and gets Vrbo, Airbnb, Booking, and Google together.
- **Travel-planning & sourcing agents** — Give your AI agent a dependable accommodation tool: “house with a pool near Murter, July 13–20, 2 adults + 2 kids” → real, normalized Vrbo results via the native MCP server.

---

## Code examples by language

Six languages, each in its own folder under [`examples/`](examples/). Every snippet is one screen, uses the language's standard library or a single zero-friction dependency, and resolves to the same unified envelope.

- [curl](examples/curl/) · [Node.js](examples/node/) · [Python](examples/python/) · [Go](examples/go/) · [Ruby](examples/ruby/) · [PHP](examples/php/)

---

## Recipes

Ready-made automations built on Vrbo data — importable n8n workflows and portable AI-agent skills. See [`recipes/`](recipes/) and the full [travel-workflows](https://github.com/scoutingapi/travel-workflows) repo, or browse them rendered at [https://scoutingapi.com/workflows](https://scoutingapi.com/workflows).

---

## Pricing & credits

Every call bills against a credit balance. **Failed, empty and blocked calls are never billed**, and `scout_test_` sandbox calls are always free. The exact, current per-endpoint costs live on the [pricing page](https://scoutingapi.com/pricing) and in the machine-readable [openapi.json](https://api.scoutingapi.com/openapi.json) — this repo stays number-free so it never drifts.

---

## FAQ

### Does Vrbo have a public API?

No. Vrbo (part of Expedia Group) does not offer a self-serve public API. The only official access is connectivity onboarding for property managers through an approved channel manager or connectivity provider — gated, and built for PMs, not developers. ScoutingAPI is the self-serve alternative: live Vrbo search, availability, and pricing through one well-documented API, no partner application required.

### Do I need a channel manager or connectivity provider to use this?

No. That requirement applies to Vrbo’s own connectivity program for property managers. ScoutingAPI sits in front of the public listing data, so you just sign up, get a Bearer key, and call /v1/search — no connectivity provider, no channel-manager contract, no approval queue.

### How do I get a Vrbo API key?

Sign up, verify your email, and your key (scout_live_… for production, scout_test_… for the sandbox) is in your dashboard immediately — no sales call, no approval queue. Add it as a Bearer token and make your first Vrbo call in under five minutes.

### How do I get Vrbo and Airbnb data in one call?

Pass both platforms in a single request — platforms=vrbo,airbnb (or platforms: ["vrbo","airbnb"] in the SDK). You get back one array of properties in the same unified schema, with each item tagged by platform. It’s the cross-platform view Vrbo’s closed ecosystem can’t give you on its own.

---

## Related repositories

Part of the ScoutingAPI open resource set — one unified accommodation-data API across Airbnb, Booking.com, Vrbo and Google Hotels, with a REST API, a native MCP server, and importable workflows.

- [airbnb-api](https://github.com/scoutingapi/airbnb-api)
- [booking-com-api](https://github.com/scoutingapi/booking-com-api)
- [google-hotels-api](https://github.com/scoutingapi/google-hotels-api)
- [hotel-api](https://github.com/scoutingapi/hotel-api)
- [travel-api](https://github.com/scoutingapi/travel-api)
- [travel-skills](https://github.com/scoutingapi/travel-skills)
- [hotel-mcp](https://github.com/scoutingapi/hotel-mcp)
- [travel-workflows](https://github.com/scoutingapi/travel-workflows)

- Website: <https://scoutingapi.com> · Docs: <https://scoutingapi.com/docs> · Status: <https://status.scoutingapi.com>

---

**Get your free key — no card → <https://scoutingapi.com/signup>** · [Docs](https://scoutingapi.com/docs) · [Pricing](https://scoutingapi.com/pricing) · [Status](https://status.scoutingapi.com)

Built with [ScoutingAPI](https://scoutingapi.com) — trusted, ToS-clean, real-time accommodation data across Airbnb, Booking.com, Vrbo and Google Hotels, normalized to one schema. REST + a native MCP server.

> ScoutingAPI is an independent service and is not affiliated with or endorsed by Vrbo. Platform names are trademarks of their respective owners.
