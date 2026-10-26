# Food It Forward

**Find the food. Pool the purchase. Fund the need. Get it delivered.** Powered by Backhaul Direct.

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
- `dist/exchange.js`: matching, pooled purchases, carrier offers, onboarding, custody and general-fund allocation.
- `dist/style.css`, `dist/network.css`, `dist/funding.css` and `dist/exchange.css`: base and Backhaul Direct interface styles.
- `checks/check.mjs`: dependency-free smoke and business-rule checks.

## Current limits

The message board, listings, pledges and receipts are saved in browser localStorage. There is no shared backend, live chat service, payment collection or production account authentication. Repository visibility controls access to the source code; it does not connect the prototype to live services.


## Order funding and leaderboard

Order funding supports food purchases by food banks, community groups and individuals. Purchasers can create campaigns with quantity, unit price and a separate transportation budget. Sponsors choose food only, transportation only or both; each amount stays assigned to its purpose. Pending contributions reserve funding space but do not count as confirmed or delivered impact. Linked purchase listings expose a Fund the order action. Funding does not reserve inventory or place a purchase order.

The Impact funding leaderboard ranks confirmed contributions across orders and delivery campaigns, with filters for all funding, food purchases and transportation. Pending pledges and canceled campaigns are excluded; matching support is credited once to the matching sponsor. Milestones use the selected category's cumulative confirmed dollars. Completed-delivery impact remains separate.

General donations: the DONATE button opens a one-time, unrestricted demo pledge form. Operations can confirm or release pending pledges. Confirmed gifts enter the general fund and the Impact leaderboard once; they remain unallocated until Operations assigns them to an eligible campaign. Allocation reduces that campaign's gap without crediting the donor twice or adding delivered pounds. There is no live payment collection, recurring billing, or tax receipt.

## Exchange workflows

- **Matches & needs:** food banks can save standing needs with keywords, location, radius, temperature, quantity and shelf-life requirements. In-app alerts identify compatible available offers. Distances use a small demo city map and are approximate; appointments and unknown shelf life require review.
- **Shared purchases:** join a pooled order, hold available pallets, compare food plus shared freight minus confirmed support, and see each participant's remaining balance. Operations confirms the supplier and recipients, creates one linked delivery, and records simulated buyer payments. Funding and inventory holds remain separate.
- **Carrier marketplace:** submit paid or donated lane offers, compare carrier capability, post return-trip or spare capacity, and record an Operations-reviewed award. A quote change places funded deliveries on review. No carrier is actually booked.
- **Network:** register organizations, attach local documents and complete a demo partner-review checklist. New partner records start pending. Review status is illustrative, not independent verification.
- **Pickup & receipt:** new exchange deliveries require a reviewed carrier, route review, lot/reference, BOL and confirmed purchase/transport funding before release. Pickup and receiving records preserve signatures, dates, temperatures and actual pounds. Accepted delivery requires POD and confirmation of every recipient; an issue holds the load without increasing impact.
- **General fund:** configure a demonstration recipient and approver, then allocate confirmed unrestricted gifts to food or freight. The allocation trail links the donor, campaign, purpose and approval. Returned or canceled allocations restore the available fund balance. General gifts and matching support are credited once; buyer payments do not count as donations.
- **Recurring pickups:** save a 7- or 14-day plan and draft its next delivery. Each draft requires fresh food availability, capacity, funding and route review. This does not run a background scheduler.
- **Urgent rescue:** paste labeled BOL text to prefill a surplus/rejected-load offer and confirm authorization and food-condition review. This is text parsing, not PDF/image OCR.

## Try the new workflow

1. In **Food & Needs → Matches & needs**, inspect a standing need and its compatible offers.
2. Open **Shared purchases**, join the remaining three pallets of rice, then switch the demo role to **BHD Operations** and confirm the pool.
3. Request transportation. In **Carrier marketplace**, submit and review a compatible offer for the linked delivery.
4. Confirm pending food support and record the remaining simulated buyer balance from the shared-purchase card. Attach a BOL, complete route review and release pickup. The fixture at `checks/fixtures/demo-bol.txt` is fictional test content.
5. Record pickup, attach proof of delivery, and record the accepted pounds received to update completed impact. Separately, use **DONATE**, confirm a gift as Operations, set the demonstration fund recipient, and allocate the gift to an open food or freight campaign to explore the allocation trail.

Documents are limited to PDF, PNG, JPEG, WebP or text, 500 KB each and 2 MB total. All documents, reviews, alerts, offers, signatures and payment confirmations stay in this browser. Role selection is not authentication. Live use still requires a shared server/database, secure organization accounts and permissions, payment processing/reconciliation, secure document storage, notification services, and operational review. Existing seed shipments keep their original simplified demo workflow; newly created exchange shipments use the expanded evidence gates.
