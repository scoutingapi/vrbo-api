<!-- generated: DO NOT EDIT BY HAND — produced by apps/web/scripts/export-github-repos.ts from content/workflows/comp-set-benchmark.ts. Edit the config + re-run. -->

# Competitor rate & availability benchmark → report

For a defined comp-set of listings, pull each one’s price and day-by-day availability, then benchmark your own listing against the set — where your rate ranks, the cheapest and median rates, and an occupancy signal from how many dates each comp has open. It fans the comp-set out, calls GET /v1/price and GET /v1/availability per listing, and correlates both into one report. A revenue-management staple, on a schedule.

## How it works

1. **Define the comp-set and your listing** — List the platform, the comma-separated listing ids for the whole comp-set (including your own), which id is yours, and the stay dates.
2. **Price every listing in the set** — The workflow fans the comp-set out and calls GET /v1/price for each listing and the dates, returning a real total per competitor.
3. **Check each listing’s availability** — It also calls GET /v1/availability per listing over the window, so occupancy density (how many dates each comp has open) feeds the benchmark.
4. **Build and deliver the benchmark** — A Code node correlates price and availability by listing, ranks the rates, flags where you sit versus the cheapest and median, and posts the report to Slack — swap for email or a Google Sheet for a weekly digest.

## Get it

- **AI-agent skill + n8n workflow:** [comp-set-benchmark in travel-workflows](https://github.com/stayingapi/travel-workflows) · rendered detail page: [https://stayingapi.com/workflows/comp-set-benchmark](https://stayingapi.com/workflows/comp-set-benchmark)
- **Endpoints used:** `price`, `availability`, `listing`

Failed/empty calls are free; sandbox calls cost 0. Costs: [https://stayingapi.com/pricing](https://stayingapi.com/pricing).

---

Back to the [vrbo-api README](../README.md)
