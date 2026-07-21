<!-- generated: DO NOT EDIT BY HAND — produced by apps/web/scripts/export-github-repos.ts from content/workflows/portfolio-feed.ts. Edit the config + re-run. -->

# Portfolio price & occupancy feed

Owners and property managers watch a fixed set of listings — their own units, or the ones a client cares about — and want one daily readout instead of opening each app. This feed takes your saved "platform:listingId" set, and for each listing pulls full detail (GET /v1/listing/{platform}/{id}), a real nightly price for your dates (GET /v1/price) and the latest reviews (GET /v1/reviews), then consolidates everything into a single report you can drop into Slack, email, a Google Sheet or a BI tool — the same shape across Airbnb, Booking.com and Vrbo.

## How it works

1. **List the portfolio and the dates** — Set your saved listings as "platform:listingId" pairs plus the check-in / check-out to price against. A Code node fans the set out into one item per listing.
2. **Pull detail, price and reviews per listing** — For each listing the pipeline calls GET /v1/listing/{platform}/{id} (name, rating, amenities), GET /v1/price (a real nightly + total for your dates) and GET /v1/reviews (the latest few).
3. **Consolidate into one digest** — A Code node correlates the three responses per listing, computes the portfolio median nightly, and formats one report — price, rating and recent-review count per listing.
4. **Deliver daily** — Post the digest to Slack or email, or append rows to a Google Sheet / BI feed for tracking over time. Runs on a daily schedule.

## Get it

- **AI-agent skill + n8n workflow:** [portfolio-feed in travel-workflows](https://github.com/stayingapi/travel-workflows) · rendered detail page: [https://stayingapi.com/workflows/portfolio-feed](https://stayingapi.com/workflows/portfolio-feed)
- **Endpoints used:** `listing`, `price`, `reviews`

Failed/empty calls are free; sandbox calls cost 0. Costs: [https://stayingapi.com/pricing](https://stayingapi.com/pricing).

---

Back to the [vrbo-api README](../README.md)
