<!-- Rapider Official App SOW & Specification | App #176: Hotel Revenue & Yield Management (hotel-revenue-and-yield-management) | Domain: HSP -->

# #176 Hotel Revenue & Yield Management (`hotel-revenue-and-yield-management`) — Scope of Work (SOW)

- **App Number & Name:** `#176` — Hotel Revenue & Yield Management
- **Proposed App Key:** `hotel-revenue-and-yield-management`
- **Suite / Domain Key & Model Prefix:** `HSP` (`Hsp*`)
- **Function Category:** 18. Hospitality, Restaurants & Travel
- **Representative Product (`P1`):** IDeaS Revenue Solutions
- **Combined Feature Catalog:** [../combined-features/176-hotel-revenue-and-yield-management-features.md](../combined-features/176-hotel-revenue-and-yield-management-features.md)
- **Target Release Posture:** Open-Pricing Revenue Management System (RMS), Comp-Set Rate Shopper, OTA Parity Monitor, Orphan-Gap Hurdles & Total-Profit Group Displacement Microapplication

---

## 1. Executive Outcome & Target Audience

### 1.1 Business Problem Solved
Hotels, resorts, and vacation rental portfolios leave 8%–18% of annual accommodation profit on the table when room pricing relies on static seasonal tables or gut-feel manual tweaks—selling out concert/convention weekends months early at cheap rack rates, leaving unsellable 1-night orphan gaps between stays, missing silent OTA rate-parity undercuts that cannibalize commission-free direct bookings, and accepting discounted group room blocks that displace higher-spending transient guests. **Rapider Hotel Revenue & Yield Management (`hotel-revenue-and-yield-management`)** provides an explainable, science-driven Commercial & Yield Operating System unifying 365-day On-The-Books (OTB) pickup pace, live Comp-Set rate shopping, OTA parity detection, *Open Pricing* floor/ceiling guardrails, orphan-gap `MinLOS` automation, and Total-Profit (`TRevPAR`/`NRevPAR`) group displacement analysis—publishing approved dynamic rates and restrictions directly into `#169 Hotel PMS` and `#172 Vacation Rental Management`.

### 1.2 Target Personas & Progressive Disclosure
- **SME Fast-Path Defaults (Boutique Hotels, Independent Inns, 10–50 Unit STR Operators):** Activate in minutes by setting `minFloorRate` and `maxCeilingRate` per room type/listing, linking 3–5 local competitors, enabling automated orphan-gap `MinLOS` relaxation, and reviewing explainable Co-Pilot daily rate recommendations on a single 365-day calendar.
- **Enterprise Progressive Disclosure (Cluster Revenue Directors, Resort Commercial Teams, Multi-Property Asset Managers):** Unlock multi-property exception-first morning workbenches, segment/channel *Open Pricing* (`NRevPAR` net of OTA commissions), Last-Room-Value (LRV) stay-through hurdles (`CTA`, `CTD`, `MinLOS`), `HspGroupDisplacementEval` walk-away calculators (factoring `#170` F&B banquet margin vs. `#169` variable room cost), below-walk-away Home `WorkItem` governance, `MPI`/`ARI`/`RGI` market-share indexing, and rolling 30/60/90-day `FinBudget` forecast snapshots.

### 1.3 Measurable Business Outcomes
- **+7% to +15% Sustained `RevPAR` & `NRevPAR` Lift:** Dynamic compression shielding, segment *Open Pricing*, and high-commission OTA channel stop-sells during peak demand capture maximum willingness-to-pay.
- **85% Reduction in Daily Manual Pricing Time:** Bounded Autopilot handles routine within-guardrail adjustments automatically while surfacing only high-impact pickup anomalies and parity violations on `#/recommendations-queue`.
- **100% Profit-Accretive Group Contracting:** Every definite `#169` `HspGroupBlock` quote is benchmarked against displaced transient margin + ancillary F&B profit before contract signature.

### 1.4 Benchmark Summary (`P1`–`P6`)
Synthesizes the unconstrained demand science, LRV hurdles, and Total-Profit group displacement of **`P1` IDeaS G3 RMS**, independent segment/channel *Open Pricing* and web regret/denial signals of **`P2` Duetto**, live Comp-Set rate shopping, parity monitoring, and OTB pace BI of **`P3` Lighthouse**, agile hotel + STR orphan-gap `MinLOS` automation of **`P4` PriceLabs**, total-resort ancillary yield forecasting of **`P5` Infor EzRMS**, and enterprise `CTA`/`CTD` restriction & dynamic room-upgrade pricing of **`P6` Oracle Hospitality Revenue / Nor1**.

---

## 2. In-Scope, Out-of-Scope & Suite Ownership Boundaries

### 2.1 In-Scope Capabilities
1. 365-day On-The-Books (OTB) occupancy, `ADR`, `RevPAR`, `NRevPAR`, `1d/7d/30d` pickup pace vs. STLY, unconstrained demand & booking regret/denial modeling (`HspDemandForecastDay`), and compression event signals (`HspMarketEventSignal`).
2. Weighted Competitive Set (*Comp Set*) rate shopping across `1/2/3+` night LOS and automated Direct-vs-OTA rate-parity undercut detection (`HspCompSetSnapshot`).
3. *Open Pricing* strategy blueprints (`HspRateStrategy`) enforcing hard `Decimal128` `minFloorRate` / `maxCeilingRate` guardrails, room-category differential curves, channel commission adjustments, and Autopilot daily step caps.
4. Explainable daily rate, room-upgrade supplement, and restriction (`MinLOS`, `MaxLOS`, `CTA`, `CTD`, orphan-gap) recommendations (`HspYieldRecommendation`) with Co-Pilot / Bounded Autopilot publishing (`HspRateCalendarOverride`).
5. Total-Profit Group Block Displacement & Walk-Away Rate evaluation (`HspGroupDisplacementEval`), `MPI`/`ARI`/`RGI` benchmarking, and rolling 30/60/90-day forecast locks synced with `budgeting`.

### 2.2 Out-of-Scope Capabilities (Delegated to Adjacent Rapider Apps)
- **Front-desk check-in/out, physical room assignment, housekeeping boards, guest folios, and night audits:** Owned by `#169 Hotel Property Management System (PMS)`.
- **Vacation rental smart-lock PINs, cleaner photo turnovers, and homeowner trust statements:** Owned by `#172 Vacation Rental Management`.
- **Group BEO sales pipeline stages & legal contract redlining:** Owned by `crm` (`CrmOpportunity`) and `#006` CLM (`#176` computes the `walkAwayRate` and displacement math for those deals).
- **Marketing email/ad campaign execution:** Owned by `campaigns` (`MktCampaign`) and `email` (`MktEmailMessage`).

### 2.3 Cross-Suite Ownership & Integration Contract

| Domain / App | Owns (Canonical Models) | Integration Contract with `hotel-revenue-and-yield-management` |
| :--- | :--- | :--- |
| **`hotel-revenue-and-yield-management` (`#176` — This App)** | `HspRateStrategy`, `HspDemandForecastDay`, `HspCompSetSnapshot`, `HspMarketEventSignal`, `HspYieldRecommendation`, `HspRateCalendarOverride`, `HspGroupDisplacementEval` | Owns demand forecasting, comp-set parity intelligence, Open Pricing optimization, group displacement math, and published rate/restriction overrides. |
| **`hotel-property-management-system-pms` (`#169` — HSP)** | `HspProperty`, `HspRoomType`, `HspHotelReservation`, `HspGroupBlock` | `#176` consumes `#169` booking/cancellation/night-audit events for OTB pace and publishes `hsp.yield.rate_override_published` (BAR, upgrade supplements, `MinLOS`/`CTA`/`CTD`) + `HspGroupDisplacementEval` walk-away rates back to `#169`. |
| **`vacation-rental-management` (`#172` — HSP)** | `HspRentalListing`, `HspRentalBooking` | `#176` consumes STR booking pace and publishes dynamic nightly pricing & orphan-gap `MinLOS` overrides to `HspRentalListing`. |
| **`crm` (`CRM` Suite)** | `CrmAccount`, `CrmOpportunity` | Evaluates corporate negotiated `CrmAccount` LRA production and scores group RFP `CrmOpportunity` displacement profitability. |
| **`budgeting` (`FIN`) & `campaigns` (`MKT`)** | `FinBudget`, `MktEvent`, `MktCampaign` | Benchmarks 30/60/90-day room revenue forecasts against `FinBudget`; ingests `MktEvent` demand signals; hands off shoulder-night promo briefs to `MktCampaign`. |
| **Rapider Platform Services** | Identity/RBAC, Home `WorkItem`, `projectChannelMessage`, Kafka/OpenWhisk | Routes floor-breach overrides, `> maxAutopilotStepPct` jumps, and below-walk-away group quotes via Home `WorkItem`s; posts AI morning pickup briefings in `projectChannelMessage`. |

---

## 3. Primary Web Pages & Sidebar Navigation Architecture

To comply strictly with the **Rapider Minimum 3 Items Sidebar Rule**, all visible pages are organized into **3 sidebar sections (`Commercial Pulse`, `Pricing & Hurdles`, `Strategy & Governance`) containing 3 visible items each (9 visible menu items total)**. Detail views and creation/edit drawers set `displayOnMenu: false`.

| # | Route | Page Title | Sidebar Section | Menu Visible | Key Components & UX |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | `dashboard` | Portfolio Commercial Pulse | `Commercial Pulse` | `true` (Order 1) | KPI cards (`countSWR`): 30-Day OTB `RevPAR` vs. STLY, `NRevPAR`, Portfolio `RGI` Index, Active Parity Undercuts, Pending Co-Pilot Recommendations, pickup pace chart. |
| 2 | `pickup-forecast` | 365-Day Pickup & Demand | `Commercial Pulse` | `true` (Order 2) | Searchable `HspDemandForecastDay` horizon table (`findSWR`), `#activeFilterTagsBar` with `Clear all`, `1d/7d/30d` pickup deltas, compression badges, clickable stay date -> `stay-date-detail`. |
| 3 | `compset-parity` | Comp-Set Shopper & Parity | `Commercial Pulse` | `true` (Order 3) | `HspCompSetSnapshot` matrix comparing Direct vs. OTA vs. Weighted Competitors (`1n/2n/3n` LOS) with red `PARITY_UNDERCUT` alert chips and OTA market-manager contact (`<rapider-phone-input>`). |
| 4 | `recommendations-queue` | Co-Pilot Yield Workbench | `Pricing & Hurdles` | `true` (Order 4) | Exception-first `<rapider-kanban>` board (`NEW_OPPORTUNITY`, `GUARDRAIL_APPROVAL_NEEDED`, `APPROVED_PUBLISHING`, `PUBLISHED_LIVE`, `DISMISSED_LOCKED`) with bulk approve & "Why This Rate?" chips. |
| 5 | `rate-calendar` | 365-Day Rate & LOS Calendar | `Pricing & Hurdles` | `true` (Order 5) | Interactive room-type / STR-listing x stay-date grid (`HspRateCalendarOverride`) showing live BAR, `MinLOS`, `CTA`/`CTD`, orphan-gap badges, and manual lock icons. |
| 6 | `group-displacement` | Group Displacement & Quotes | `Pricing & Hurdles` | `true` (Order 6) | `HspGroupDisplacementEval` ledger (`CrmOpportunity` / `HspGroupBlock`), displaced transient `\$`, F&B ancillary margin, `walkAwayRate`, clickable `#DSP-...` -> `displacement-detail`. |
| 7 | `rate-strategies` | Open Pricing & Guardrails | `Strategy & Governance` | `true` (Order 7) | `HspRateStrategy` catalog configuring `Decimal128` `minFloorRate` / `maxCeilingRate`, Autopilot mode (`CO_PILOT` vs. `BOUNDED_AUTOPILOT`), room-type differentials, and orphan-gap rules. |
| 8 | `events-signals` | Compression Events & Signals | `Strategy & Governance` | `true` (Order 8) | `HspMarketEventSignal` calendar (conventions, stadium concerts, holidays) with demand multiplier tiers and minimum-rate lock protections. |
| 9 | `budget-attribution` | Forecast vs. Budget & RGI | `Strategy & Governance` | `true` (Order 9) | Rolling 30/60/90-day forecast accuracy (`MAPE`) vs. `FinBudget`, `MPI`/`ARI`/`RGI` trend scorecard, and human-override vs. algorithm lift audit. |
| 10 | `stay-date-detail` | Stay-Date Yield 360 | *(Hidden)* | `false` | Deep stay-date cockpit (`?id=...`): segment booking curve, unconstrained regrets/denials, comp-set bar chart, explainable AI factor breakdown (`projectChannelMessage`), `Back to Pickup`. |
| 11 | `displacement-detail` | Group Displacement Analysis | *(Hidden)* | `false` | Full `HspGroupDisplacementEval` simulator (`?id=...`): day-by-day transient displacement waterfall, F&B/meeting profit inputs, AI shoulder-date counter-offer, `Back to Quotes`. |
| 12 | `rate-override-drawer` | Override Rate / Restriction | *(Hidden)* | `false` | Sliding drawer to set stay-date `Decimal128` rate, `MinLOS`, `CTA`/`CTD`, and mandatory override reason code (spawning Home `WorkItem` if breaching floor/ceiling), `try/catch/finally` reset, auto-close. |
| 13 | `displacement-drawer` | Run New Group RFP Evaluation | *(Hidden)* | `false` | Sliding drawer evaluating proposed group room nights, requested rate, and F&B ancillary spend against live OTB forecast with instant `walkAwayRate` computation. |

---

## 4. Canonical Data Models (`Hsp*` — 7 Models)

All models omit `projectId`, use platform UUIDs (`00000000-xxxx-xxxx-xxxx-xxxxxxxxxxxx` in seed data), enforce optimistic `version`, and store all rates, guardrails, indexes, and displacement profit figures as `Decimal128`.

| Model Name | Key Fields & Types | Relationships & External Refs | Invariants & Lifecycle |
| :--- | :--- | :--- | :--- |
| **`HspRateStrategy`** | `strategyCode` (String, unique), `name` (String), `targetAssetType` (`HOTEL_ROOM_TYPE`, `VACATION_RENTAL_LISTING`), `automationMode` (`CO_PILOT_SUPERVISED`, `BOUNDED_AUTOPILOT`), `minFloorRate` (`Decimal128`), `baseReferenceRate` (`Decimal128`), `maxCeilingRate` (`Decimal128`), `maxDailyAutopilotStepPct` (`Decimal128`), `enableOrphanGapRelax` (Boolean), `orphanGapMaxNights` (Int), `otaMarketManagerPhone` (String E.164), `status` (`ACTIVE`, `PAUSED`, `ARCHIVED`) | `propertyId` -> `HspProperty.id` (`#169`, optional), `roomTypeId` -> `HspRoomType.id` (`#169`, optional), `rentalListingId` -> `HspRentalListing.id` (`#172`, optional) | `0 < minFloorRate <= baseReferenceRate <= maxCeilingRate`; Autopilot may never publish below `minFloorRate` or above `maxCeilingRate`. |
| **`HspDemandForecastDay`** | `stayDate` (Date), `sellableCapacity` (Int), `otbBookedUnits` (Int), `otbOccupancyPct` (`Decimal128`), `pickupLast1d` (Int), `pickupLast7d` (Int), `stlyOccupancyPct` (`Decimal128`), `unconstrainedDemandUnits` (`Decimal128`), `regretsAndDenialsCount` (Int), `currentAdr` (`Decimal128`), `forecastRevPar` (`Decimal128`), `netRevPar` (`Decimal128`), `mpiIndex` (`Decimal128`), `ariIndex` (`Decimal128`), `rgiIndex` (`Decimal128`) | `strategyId` -> `HspRateStrategy.id`, `budgetId` -> `FinBudget.id` (optional), `activeEventSignalIds` -> `HspMarketEventSignal.id[]` | Unique per `(strategyId, stayDate)`; `otbOccupancyPct == (otbBookedUnits / sellableCapacity) * 100`. |
| **`HspCompSetSnapshot`** | `stayDate` (Date), `lengthOfStayNights` (Int), `directBrandRate` (`Decimal128`), `lowestOtaRate` (`Decimal128`), `lowestOtaChannelName` (String), `compSetWeightedMedianRate` (`Decimal128`), `compSetMinRate` (`Decimal128`), `compSetMaxRate` (`Decimal128`), `competitorsSoldOutCount` (Int), `parityStatus` (`IN_PARITY`, `PARITY_UNDERCUT`, `DIRECT_ADVANTAGE`), `undercutDeltaAmount` (`Decimal128`) | `strategyId` -> `HspRateStrategy.id` | If `directBrandRate - lowestOtaRate > parityTolerance`, sets `parityStatus = PARITY_UNDERCUT`. |
| **`HspMarketEventSignal`** | `eventCode` (String, unique), `title` (String), `startDate` (Date), `endDate` (Date), `impactTier` (`LOW`, `MODERATE`, `HIGH_COMPRESSION`, `SELLOUT_PEAK`), `demandMultiplier` (`Decimal128`), `protectMinLos` (Int) | `propertyId` -> `HspProperty.id` (optional), `linkedMktEventId` -> `MktEvent.id` (optional) | `endDate >= startDate`; `demandMultiplier >= 1.00` on compression events. |
| **`HspYieldRecommendation`** | `stayDate` (Date), `currentPublishedRate` (`Decimal128`), `recommendedRate` (`Decimal128`), `recommendedUpgradeSupplement` (`Decimal128`), `deltaPct` (`Decimal128`), `recommendedMinLos` (Int), `recommendedCta` (Boolean), `recommendedCtd` (Boolean), `lastRoomValueHurdle` (`Decimal128`), `confidenceScore` (`Decimal128`), `explanationDrivers` (String[]), `opportunityScore` (`Decimal128`), `status` (`NEW_OPPORTUNITY`, `GUARDRAIL_APPROVAL_NEEDED`, `APPROVED_PUBLISHING`, `PUBLISHED_LIVE`, `DISMISSED_LOCKED`) | `strategyId` -> `HspRateStrategy.id`, `forecastDayId` -> `HspDemandForecastDay.id` | Every recommendation carries non-empty `explanationDrivers`; if `abs(deltaPct) > maxDailyAutopilotStepPct`, Bounded Autopilot routes to `GUARDRAIL_APPROVAL_NEEDED` + Home `WorkItem`. |
| **`HspRateCalendarOverride`** | `stayDate` (Date), `effectiveBarRate` (`Decimal128`), `upgradeSupplementRate` (`Decimal128`), `minLos` (Int), `maxLos` (Int), `closedToArrival` (Boolean), `closedToDeparture` (Boolean), `stopSellHighCommissionOta` (Boolean), `isOrphanGapRelaxed` (Boolean), `isManualLock` (Boolean), `overrideReasonCode` (String), `publishedAt` (DateTime) | `strategyId` -> `HspRateStrategy.id`, `sourceRecommendationId` -> `HspYieldRecommendation.id` (nullable) | Manual overrides breaching `minFloorRate` or `maxCeilingRate` remain un-published until Director approves Home `WorkItem`. |
| **`HspGroupDisplacementEval`** | `evalCode` (String, unique), `groupName` (String), `arrivalDate` (Date), `departureDate` (Date), `requestedRoomNightsTotal` (Int), `proposedGroupRate` (`Decimal128`), `displacedTransientRoomNights` (`Decimal128`), `displacedTransientRevenue` (`Decimal128`), `ancillaryFbNetContribution` (`Decimal128`), `variableHousekeepingCostDelta` (`Decimal128`), `walkAwayRate` (`Decimal128`), `netProfitDelta` (`Decimal128`), `verdict` (`ACCRETIVE_RECOMMEND_ACCEPT`, `MARGINAL_COUNTER_OFFER`, `DISPLACES_PROFIT_REQUIRES_APPROVAL`), `status` (`DRAFT`, `APPROVED_FOR_QUOTE`, `PENDING_DIRECTOR_WORKITEM`, `REJECTED`) | `propertyId` -> `HspProperty.id` (`#169`), `groupBlockId` -> `HspGroupBlock.id` (`#169`, optional), `opportunityId` -> `CrmOpportunity.id` (`crm`) | `netProfitDelta == (requestedRoomNightsTotal * proposedGroupRate) + ancillaryFbNetContribution - displacedTransientRevenue - variableHousekeepingCostDelta`; if `proposedGroupRate < walkAwayRate`, converting quote to definite requires approved Home `WorkItem`. |

---

## 5. Core End-to-End User Journeys

### Journey 1: SME Fast-Path — Compression Spike Detection -> Co-Pilot Approval -> Live `#169` & `#172` Rate Push
1. Overnight, an announced stadium concert (`HspMarketEventSignal`: `SELLOUT_PEAK`) + `+18` room-night 24-hour pickup pushes Friday/Saturday unconstrained demand to `118%` of capacity on `HspDemandForecastDay`.
2. On `#/recommendations-queue` (`<rapider-kanban>`), `#176` surfaces a high-opportunity card recommending King Deluxe BAR move from `\$219.00` -> `\$289.00` (`+31.9%`), `MinLOS = 2`, and `stopSellHighCommissionOta = true`, listing exact drivers (*"+18 1-day pickup, Comp Set median \$295, Stadium Concert Peak"*).
3. Because `+31.9%` exceeds the `20%` Autopilot single-day step cap, the Revenue Manager reviews and clicks **Approve & Publish**—emitting `hsp.yield.rate_override_published` so `#169` Hotel PMS updates its BAR, `MinLOS`, and OTA channel rates within 5 seconds.

### Journey 2: Automated Orphan-Night Gap Relaxation Across Hotel & Vacation Rentals
1. On `#/rate-calendar`, a `#172` luxury 3BR Beach Condo (`default MinLOS = 4 nights`) has a Monday checkout and a Wednesday check-in—leaving an unsellable `2-night` Tuesday/Wednesday orphan gap.
2. Because `HspRateStrategy.enableOrphanGapRelax == true` (`orphanGapMaxNights = 2`), workflow `wf-hsp-orphan-gap-optimizer` automatically lowers `minLos` on Monday/Tuesday to `2 nights` with a `+10%` short-stay rate premium (`\$495.00/night` within ceiling guardrails) and pushes the update to `#172` (`HspRentalListing`), capturing `\$990.00` that would otherwise sit dark.

### Journey 3: Total-Profit Group Block Displacement & AI Shoulder-Date Counter-Offer
1. A corporate client (`CrmOpportunity` `OPP-7740`) requests `40 rooms/night` for Tue–Thu during a busy October conference week at `\$195.00/night` plus a `\$6,000.00` banquet dinner (`\$3,900.00` net `#170` F&B contribution).
2. In `displacement-drawer`, the Sales Manager runs `evaluateGroupDisplacement`: `#176` calculates that `52` transient room nights at `\$285.00` ADR would be displaced, yielding `walkAwayRate = \$218.50` and `netProfitDelta = -\$2,820.00` (`DISPLACES_PROFIT_REQUIRES_APPROVAL`).
3. Simultaneously, the AI Counter-Offer Shifter in `projectChannelMessage` notes that shifting the group 2 days earlier (`Sun–Tue`) displaces `0` transient rooms (`walkAwayRate = \$142.00`, `netProfitDelta = +\$6,360.00`!). If the client insists on `Tue–Thu` at `\$195.00`, `#176` gates quote approval behind a Director of Revenue Rapider Home `WorkItem`.

### Journey 4: OTA Rate-Parity Undercut Alert & Guardrail Floor-Breach Governance
1. `#/compset-parity` flags a `PARITY_UNDERCUT` on Nov 14: Direct Brand.com is `\$249.00` while a third-party wholesaler on an OTA is undercutting at `\$231.00` (`-\$18.00`). The Revenue Manager uses the OTA Market Manager contact (`<rapider-phone-input>`) and closes the wholesaler promo code.
2. Later, a junior analyst attempts to manually override a slow January Sunday rate in `rate-override-drawer` to `\$119.00`—below the `\$139.00` `minFloorRate` on `HspRateStrategy`; `#176` blocks immediate publication and creates a Home `WorkItem` requiring Cluster Revenue Director approval.

### Journey 5: Multi-Property Filter Search & Click-Through Navigation State Preservation
1. On `#/pickup-forecast`, the Cluster Revenue Manager filters `Impact: "HIGH_COMPRESSION"` and searches `Suite`, clicks stay date `2026-11-14` to open `#/stay-date-detail?id=...` (inspecting the booking curve, regrets/denials, and Comp-Set chart), and clicks **Back to Pickup & Demand**—returning cleanly to `#/pickup-forecast` with all `#activeFilterTagsBar` chips preserved.

---

## 6. Consolidated Feature Priorities & Work Packages

### `P0` Foundation Work Packages (Mandatory MVP Launch)
- **WP-P0-1: 365-Day OTB Pickup Pace & Unconstrained Demand (`HRY-001`, `HRY-002`):** `HspDemandForecastDay` (`#/pickup-forecast`, `#/stay-date-detail`) ingesting `#169` & `#172` reservations + web regrets/denials.
- **WP-P0-2: Comp-Set Rate Shopper & OTA Parity Monitor (`HRY-005`, `HRY-006`):** `HspCompSetSnapshot` (`#/compset-parity`) with weighted competitor medians and `PARITY_UNDERCUT` alerts.
- **WP-P0-3: Open Pricing Guardrails, Recommendations & Co-Pilot/Autopilot Push (`HRY-008`, `HRY-009`, `HRY-010`):** `HspRateStrategy`, `HspYieldRecommendation`, `HspRateCalendarOverride` (`#/rate-strategies`, `#/recommendations-queue`, `#/rate-calendar`, `rate-override-drawer`), Home `WorkItem` guardrail gates, and live publish to `#169`/`#172`.
- **WP-P0-4: Group Block Displacement & Walk-Away Calculator (`HRY-013`):** `HspGroupDisplacementEval` (`#/group-displacement`, `#/displacement-detail`, `displacement-drawer`) combining transient displacement + F&B net margin.

### `P1` Scale & Enterprise Work Packages
- **WP-P1-1: Compression Event Signals, Forecast Snapshots & `RGI` Indexes (`HRY-003`, `HRY-004`, `HRY-007`):** `HspMarketEventSignal` (`#/events-signals`), 30/60/90-day `FinBudget` forecast locks (`#/budget-attribution`), and `MPI`/`ARI`/`RGI` scorecards.
- **WP-P1-2: Orphan-Gap Relaxer, Dynamic Room Upgrades & `NRevPAR` Channel Stops (`HRY-011`, `HRY-012`, `HRY-014`):** Automated gap-night `MinLOS` tuning, `#169` pre-arrival upgrade supplements, and high-commission OTA peak stop-sells.
- **WP-P1-3: Below-Walk-Away Group Gates, Wash/Overbooking & Multi-Property Workbench (`HRY-015`, `HRY-016`, `HRY-017`, `HRY-018`):** Home `WorkItem` sign-off for negative-delta group blocks, safe overbooking caps, portfolio opportunity ranking, and manual override lift attribution.

### `P2` Adjacent & Grounded AI Work Packages
- **WP-P2-1: Grounded AI Morning Pickup Briefings & Explainable Drivers (`HRY-019`, `HRY-020`):** Cited daily commercial summaries in `projectChannelMessage` and transparent factor decompositions on every recommendation.
- **WP-P2-2: AI Group Date Shifter, Shoulder Promo Triggers & LRA Reviews (`HRY-021`, `HRY-022`, `HRY-023`, `HRY-024`):** Profit-positive group arrival counter-offers, `MktCampaign` shoulder-night briefs, corporate `CrmAccount` LRA renewal analytics, and STR seasonal `MinLOS` ladders.

---

## 7. Roles, Permissions & Field-Level Governance

| Role | Permitted Actions | Restricted / Field-Level Boundaries |
| :--- | :--- | :--- |
| **Sales / Group Coordinator** | Run `HspGroupDisplacementEval` simulations for `CrmOpportunity` RFPs; view stay-date availability and recommended `walkAwayRate`. | Cannot publish transient BAR overrides; cannot approve group quotes below `walkAwayRate` without Director Home `WorkItem` sign-off. |
| **Property Revenue Analyst** | Review `#/recommendations-queue`; approve/override stay-date rates & `MinLOS` within `[minFloorRate, maxCeilingRate]`; manage `HspMarketEventSignal`s. | Cannot publish rates breaching `minFloorRate`/`maxCeilingRate` or alter Autopilot guardrail caps without Director approval. |
| **Cluster Revenue Director / GM** | Configure `HspRateStrategy` floor/ceiling guardrails & `BOUNDED_AUTOPILOT` step caps; approve floor-breach and below-walk-away group Home `WorkItem`s; lock monthly forecasts. | All guardrail edits, manual overrides, and displacement sign-offs are recorded in immutable audit logs with actor, timestamp, and reason code. |
| **Asset Manager / Hospitality Finance** | View `#/dashboard`, `#/budget-attribution` (`RevPAR`, `NRevPAR`, `RGI`, forecast `MAPE` vs. `FinBudget`), and corporate LRA production reports. | Read-only commercial oversight; cannot push live PMS rate/restriction changes. |

---

## 8. Technical APIs, Guarded Commands, Events & `requiredWorkflows`

### 8.1 Guarded Domain Commands
Every mutating command enforces `{ idempotencyKey, correlationId, expectedVersion }`:
- `hsp.yield.approveAndPublishRecommendations` — Validates each `HspYieldRecommendation` against `[minFloorRate, maxCeilingRate]`, writes `HspRateCalendarOverride`, and emits `hsp.yield.rate_override_published` to `#169` / `#172`.
- `hsp.yield.setManualStayDateOverride` — Requires `overrideReasonCode`; publishes immediately if within `[minFloorRate, maxCeilingRate]`, or routes a Rapider Home `WorkItem` if breaching floor/ceiling bounds.
- `hsp.yield.evaluateGroupDisplacement` — Computes deterministic `Decimal128` transient displacement + ancillary F&B profit + `walkAwayRate`; if quote conversion is requested below `walkAwayRate`, spawns a Director Home `WorkItem`.
- `hsp.yield.lockForecastSnapshot` — Captures an immutable 30/60/90-day room & ancillary revenue snapshot benchmarked against `FinBudget`.

### 8.2 Published & Consumed Kafka Domain Events
- **Published:** `hsp.yield.rate_override_published`, `hsp.yield.parity_violation_detected`, `hsp.yield.group_displacement_evaluated`, `hsp.yield.forecast_snapshot_locked`.
- **Consumed:** `hsp.reservation.booked`, `hsp.reservation.modified`, `hsp.reservation.cancelled`, `hsp.night_audit.completed` (from `#169`), `hsp.vrm.booking_confirmed` & `hsp.vrm.booking_cancelled` (from `#172`).

### 8.3 `requiredWorkflows` (Declared in `app.manifest.json`)
1. `wf-hsp-otb-pickup-and-yield-recompute` — Incrementally recomputes `HspDemandForecastDay` and `HspYieldRecommendation`s upon `#169`/`#172` pickup bursts or `BOUNDED_AUTOPILOT` cycles (`HRY-001`, `HRY-009`, `HRY-010`).
2. `wf-hsp-orphan-gap-optimizer` — Scans `#169` room types and `#172` STR calendars for unsellable 1–2 night gaps and publishes bounded `MinLOS` relaxations (`HRY-011`).
3. `wf-hsp-compset-parity-watchdog` — Evaluates incoming `HspCompSetSnapshot` feeds and raises `PARITY_UNDERCUT` alerts when OTAs undercut Direct Brand.com (`HRY-006`).
4. `wf-hsp-guardrail-and-displacement-workitem` — Orchestrates Rapider Home `WorkItem` approvals for floor/ceiling overrides, large Autopilot jumps, and below-walk-away group quotes (`HRY-010`, `HRY-015`).

### 8.4 Grounded Rapider AI Guardrails
- AI Morning Pickup Briefings, "Why This Rate?" Explanations, and Group Date Counter-Offers ground 100% of numbers in cited `HspDemandForecastDay`, `HspCompSetSnapshot`, and `HspGroupDisplacementEval` records within RBAC scope.
- AI **never** bypasses `minFloorRate` / `maxCeilingRate` guardrails, never approves negative-profit group blocks, and never launches `MktCampaign` discounts without explicit human confirmation.

---

## 9. Security, Privacy, Compliance & Non-Functional Requirements

- **Antitrust & Algorithmic Pricing Compliance:** Competitive set (`HspCompSetSnapshot`) ingestion uses strictly public retail OTA/Brand.com rates—zero sharing or pooling of non-public confidential occupancy, forward pace, or pricing formulas between competing hotel operators; every `HspRateStrategy` remains 100% controlled by the tenant's independent floor/ceiling guardrails.
- **Price Gouging Emergency Guardrails:** `maxCeilingRate` + emergency state-of-emergency rate-freeze toggles prevent automated algorithms from spiking hotel rates during declared natural disasters or civil evacuations.
- **Zero Guest PII Exposure in Yield Models:** Demand and pickup cubes operate on aggregated room-type/segment counts—revenue analysts never need access to guest passport numbers or personal contact PII.
- **Accessibility & Multi-Monitor Commercial UX:** WCAG 2.2 AA compliant, high-density keyboard-navigable 365-day pricing grids, and full dark/light theme support across `1440px` revenue desks, `768px` tablets, and `390px` GM mobile screens.

---

## 10. Deterministic Acceptance Criteria

1. **Sidebar Minimum-3-Items Compliance:** `app.manifest.json` defines 3 visible sidebar sections (`Commercial Pulse`, `Pricing & Hurdles`, `Strategy & Governance`) with 3 visible items each (`displayOnMenu: true`); detail and drawer routes set `displayOnMenu: false`.
2. **Hard Floor/Ceiling Guardrail Enforcement:** Bounded Autopilot clamps or holds any recommendation outside `[minFloorRate, maxCeilingRate]`, and a manual override below `minFloorRate` creates a Rapider Home `WorkItem` rather than publishing immediately.
3. **Autopilot Step-Cap Safety Gate:** A recommendation whose `abs(deltaPct)` exceeds `HspRateStrategy.maxDailyAutopilotStepPct` transitions to `GUARDRAIL_APPROVAL_NEEDED` instead of auto-publishing.
4. **Two-Way `#169` & `#172` Rate/Restriction Publish:** Approving a recommendation persists `HspRateCalendarOverride` and emits `hsp.yield.rate_override_published` carrying exact `Decimal128` `effectiveBarRate`, `upgradeSupplementRate`, `minLos`, `closedToArrival`, and `closedToDeparture`.
5. **Orphan-Gap `MinLOS` Relaxation:** A 2-night open gap between confirmed bookings on a `minLos == 4` strategy with `enableOrphanGapRelax == true` and `orphanGapMaxNights >= 2` relaxes `minLos` to `2` for those gap dates only.
6. **Deterministic `Decimal128` Group Displacement Math:** `HspGroupDisplacementEval` computes `netProfitDelta == (requestedRoomNightsTotal * proposedGroupRate) + ancillaryFbNetContribution - displacedTransientRevenue - variableHousekeepingCostDelta` to `0.01` `Decimal128` accuracy, and gates quotes below `walkAwayRate` behind a Home `WorkItem`.
7. **OTA Parity Undercut Detection:** Ingesting a `HspCompSetSnapshot` where `lowestOtaRate` undercuts `directBrandRate` beyond tolerance sets `parityStatus == PARITY_UNDERCUT` and surfaces the exact `undercutDeltaAmount`.
8. **Explainable Recommendation Invariant:** Every `HspYieldRecommendation` contains `>= 1` human-readable string in `explanationDrivers` citing concrete pickup, comp-set, or event inputs.
9. **Custom Elements Adoption:** Market-manager/contact phone fields use `<rapider-phone-input>` and `#/recommendations-queue` renders workflow stages via `<rapider-kanban>`.
10. **SWR Clean Query & Optimistic UI Standard:** Initial reads invoke `findSWR` / `countSWR` without `isDeleted` query filters, optimistically update local state + invalidate SWR cache on drawer save/delete, and reset save buttons inside `finally`.
11. **Table Action & Click-Through Navigation Standard:** Data tables omit standalone `View` buttons; clicking a Stay Date or `#DSP-...` navigates to `#/stay-date-detail?id=...` or `#/displacement-detail?id=...` without `<base href>` 404 diversion, and `Back` restores `#activeFilterTagsBar` state.
12. **Search, `#activeFilterTagsBar` & `Clear all`:** Filtering forecast dates, comp-set rows, or displacement quotes renders HTML-escaped chips in `#activeFilterTagsBar` with `✕` dismissal and `Clear all` reset.
13. **Theme & Button Contrast Compliance:** All 13 routes pass `validate_theme` in dark and light modes with `#ffffff !important` text contrast on primary and destructive buttons and zero native `window.alert`/`confirm`/`prompt`.
