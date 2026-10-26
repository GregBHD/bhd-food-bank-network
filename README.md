# BHD | Food Bank Network

Buildless HTML/CSS/JavaScript prototype. All organizations, prices, records, and impact are illustrative. No external messages, payments, or bookings are performed.

Serve the `dist/` directory using any static web server. Changes stay in browser localStorage under bhd-food-network-v2. Reset demo restores seeds. Photo uploads stay local.

Demo: approve the final produce allocation in Donors & Sponsors, pledge the remaining transportation gap, switch to BHD Operations, confirm pending funding, assign refrigerated capacity and approve route review, release for pickup, then record actual pounds received. Impact updates from completed shipments only.

Role switching demonstrates UI capabilities, not secure authorization. Production requires server-side identity and organization permissions, transaction-safe inventory and sponsorship ledgers, real payment reconciliation, secure document storage, and approved food and carrier workflows. Dates are fixed to an October 26, 2026 demonstration. Funding quotes show transportation, handling and BHD coordination separately. Quote changes hold dispatch for participant review. Cancellation retains funding until simulated reconciliation.

Design revision: matches the supplied FoodBankNetwork reference with horizontal navigation, compact white panels, navy #0B1F3A and lime #BCD84A. Official Backhaul Direct white logo is served from backhauldirect.com. Inter font has a system-font fallback.

The message board includes four channels, linked listings/shipments, search, posting, replies and browser persistence. All sample conversations are fictional; it is not live multi-user chat. A shared authenticated message store, moderation and notification service are needed for live use.

## Run locally

This is a static site with no build step or package installation. From the repository root, run:

```bash
python3 -m http.server 8000 --directory dist
```

Then open http://localhost:8000 in your browser. The logo and Inter font are loaded from external sources.

## Run the checks

With a current Node.js installation:

```bash
node checks/check.mjs
```

The checks cover funding totals, allocation limits, dispatch requirements, completed-delivery impact and page rendering.

## Project layout

- `dist/index.html`: application entry point.
- `dist/data.js`: fictional seed data and shared ledger helpers.
- `dist/app.js`: food, transportation, sponsorship and delivery workflows.
- `dist/redesign.js`: reference-style navigation, overview and message board.
- `dist/funding.js`: food-purchase campaigns, separate funding purposes and the Impact leaderboard.
- `dist/style.css`, `dist/network.css` and `dist/funding.css`: base and Backhaul Direct interface styles.
- `checks/check.mjs`: dependency-free smoke and business-rule checks.

## Current limits

The message board, listings, pledges and receipts are saved in browser localStorage. There is no shared backend, live chat service, payment collection or production account authentication. Making this repository public makes its source code available; it does not connect the prototype to live services.


## Order funding and leaderboard

Order funding supports food purchases by food banks, community groups and individuals. Purchasers can create campaigns with quantity, unit price and a separate transportation budget. Sponsors choose food only, transportation only or both; each amount stays assigned to its purpose. Pending contributions reserve funding space but do not count as confirmed or delivered impact. Linked purchase listings expose a Fund the order action. Funding does not reserve inventory or place a purchase order.

The Impact funding leaderboard ranks confirmed contributions across orders and delivery campaigns, with filters for all funding, food purchases and transportation. Pending pledges and canceled campaigns are excluded; matching support is credited once to the matching sponsor. Milestones use the selected category's cumulative confirmed dollars. Completed-delivery impact remains separate.
