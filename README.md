# Offers Bangladesh (Working Title) — Deep Product Research

> **Project Scope:** A centralized web & mobile platform aggregating all types of consumer offers — discounts, cashbacks, BOGO deals, bank card perks, MFS campaigns, telco loyalty rewards, and retail/dining/hotel promotions — launching first in **Bangladesh** with an architecture designed for **multi-country expansion**.

---

## Executive Summary & Verdict

### Verdict: **Conditional GO — With a Sharp Wedge**

Building a "centralized platform for *all* offers in Bangladesh" addresses a **real, painful, and growing problem**: offer fragmentation. As of mid-2026, Bangladesh has **52.9 million payment cards** across 56 banks/NBFIs, **240+ million MFS accounts** (bKash, Nagad, Rocket, Upay), **3 major telco loyalty ecosystems** (GPStar, Robi Elite, Banglalink Orange Club), and hundreds of thousands of Facebook-first retail and restaurant merchants. Consumers routinely leave **10%–50% savings on the table** simply because deals are buried across dozens of bank PDFs, SMS blasts, app banners, and Facebook posts.

**However, launching as a "generic everything-offers directory" on Day 1 is a well-documented startup trap.** Historical deal aggregators fail due to:
1. **Stale/expired offers** destroying user trust within 2 visits.
2. **The chicken-and-egg problem** of onboarding thousands of offline merchants before having traffic.
3. **Low switching costs** ("coupon chasers" with zero loyalty).
4. **Regulatory traps** in Bangladesh if you try to operate a cashback wallet without a Bangladesh Bank PSP license.

### The Winning Strategy (TL;DR)
1. **Start with a "Wallet-Aware" Wedge (Zero Merchant Cold-Start):** Launch by aggregating **already-existing, high-value offers** from Bangladesh's top 15 banks (Credit/Debit/Prepaid cards), 4 MFS apps (bKash, Nagad, Rocket, Upay), and 3 telcos (GPStar, Robi Elite, Orange Club). Users select *"What's in my wallet?"* (e.g., *City Bank Amex + bKash + GPStar*) and instantly see every restaurant, hotel, clothing brand, and shop where they get a discount right now, sorted by proximity.
2. **Layer AI-Powered Social Commerce Ingestion:** Bangladeshi SMEs (restaurants, clothing boutiques, resorts) announce 80%+ of their deals as **image flyers on Facebook/Instagram** (often in Banglish/Bengali). Use Vision LLMs to extract structured deals from flyers automatically.
3. **Avoid Holding User Cash Early:** Do **not** build an internal cashback wallet in Phase 1 (triggers Bangladesh Bank PSP/e-wallet regulations). Route cashback via affiliate redirects, instant promo codes, or direct MFS payouts only after regulatory clarity.
4. **Monetize via B2B Attention & Performance First:** Sponsored placements, featured Eid/Pohela Boishakh/Ramadan campaigns, merchant self-serve boosts, and affiliate commissions (Daraz, ShareTrip, GoZayaan, global travel) — before attempting consumer subscriptions.

---

## Research Document Index

| # | Document | What It Covers |
| :-: | :--- | :--- |
| **01** | [01-brainstorming-and-vision.md](./01-brainstorming-and-vision.md) | Problem framing, core product angles, "Wallet-Aware" concept, vertical breakdown, and multi-country vision. |
| **02** | [02-idea-validation-and-market-analysis.md](./02-idea-validation-and-market-analysis.md) | 2025–2026 Bangladesh market data (cards, MFS, internet, e-commerce), TAM/SAM/SOM, personas, and a 4-week lean validation playbook. |
| **03** | [03-competitor-analysis.md](./03-competitor-analysis.md) | Local BD competitors (OfferTracker BD, bKash/Nagad, GPStar/Robi/BL, Foodpanda, Daraz) + global benchmarks (ShopBack, Magicpin, The Entertainer, Honey). |
| **04** | [04-product-direction-and-roadmap.md](./04-product-direction-and-roadmap.md) | Phased roadmap (MVP -> Growth -> Scale -> International), core UX journeys, merchant portal, and i18n readiness. |
| **05** | [05-data-collection-and-aggregation.md](./05-data-collection-and-aggregation.md) | The #1 hardest problem: 5-pillar data ingestion (scrapers, Vision AI for FB flyers, merchant portal, affiliates, UGC), freshness engine, and deduplication. |
| **06** | [06-tech-stack-and-architecture.md](./06-tech-stack-and-architecture.md) | Recommended web, mobile, backend, geo-search, AI pipeline, and cloud stack optimized for lean budgets and multi-country scaling. |
| **07** | [07-cost-and-monetization.md](./07-cost-and-monetization.md) | Development & monthly operational costs (BDT & USD) at 10K / 100K / 1M MAU, revenue models, and unit economics. |
| **08** | [08-critiques-risks-and-mitigations.md](./08-critiques-risks-and-mitigations.md) | Red-team critique: why offer platforms fail, Bangladesh-specific legal/business traps, and concrete mitigations. |

---

## Key Snapshot: Bangladesh Market Opportunity (2025–2026)

| Metric | Figure (BD) | Strategic Implication |
| :--- | :--- | :--- |
| **Internet Subscribers** | ~137.7M (~77.9% penetration) | Huge digital reach; **122.3M are mobile-only**. |
| **PC / Desktop Usage** | ~11.8% of individuals | **Mobile-first** (Android priority) + mobile web SEO is mandatory. |
| **MFS Accounts** | 238M–240M+ (bKash ~67% share) | MFS cashback campaigns are the #1 mass-market deal driver. |
| **Payment Cards** | 52.9M total (40.9M Debit, 2.8M Credit, 9.3M Prepaid) | High-value urban audience; **45–48%** of domestic credit card spend is retail/department stores & dining. |
| **E-Commerce Market** | $5B–$6B/yr (+12–18% YoY) | Growing rapidly beyond Dhaka/Chattogram into district towns. |
| **Primary SME Channel** | Facebook / Instagram Pages | Traditional web scraping misses 70%+ of local shop/restaurant offers; **AI flyer ingestion** is a moat. |
