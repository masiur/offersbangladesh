# 04 — Product Direction & Roadmap

## 1. Strategic Positioning: "Start Narrow to Go Broad"

A common mistake is trying to launch Day 1 with:
- Every city in Bangladesh
- Cashback wallets
- QR redemption & POS integration
- Merchant dashboards
- International support

That leads to a bloated, half-baked product with stale data. Instead, follow a **4-Phase Expansion Playbook**:

```
Phase 1 (MVP: Months 1–3)       -> "Wallet-Aware Aggregator" (Web + PWA/Mobile) — Dhaka + National Online/Bank/MFS/Telco
Phase 2 (Growth: Months 4–9)    -> Native Apps (Android/iOS) + AI Social Flyer Radar + Community Verification + Merchant Self-Serve
Phase 3 (Monetize: Months 10–18)-> Exclusive App-Only Deals + Sponsored Boosts + Affiliate Cashback + Major BD Cities (CTG/Sylhet/etc.)
Phase 4 (Scale: Months 18+)     -> Multi-Country Expansion (Pakistan / Sri Lanka / UAE / SEA) + B2B Loyalty-as-a-Service
```

---

## 2. Core User Journeys (What Great UX Looks Like)

### Journey 1: 30-Second "My Wallet" Onboarding (No Login Required!)
- User opens the app or website. **Do NOT force account creation upfront.**
- Prompt: *"What do you pay with? Pick yours to unlock personalized deals:"*
  - **MFS:** `[bKash]` `[Nagad]` `[Rocket]` `[Upay]`
  - **Banks / Cards:** Searchable chips (`City Bank Amex`, `EBL Visa`, `BRAC Bank`, `SCB`, `DBBL`, `MTB`, `Prime`, etc. — choose Debit/Credit/Prepaid tier if known).
  - **Telco Tier:** `[GPStar]` `[Robi Elite]` `[BL Orange Club]`
- Stored locally on device (syncs to account if they sign in later via Google / Phone OTP).
- **Instant payoff:** Home feed immediately re-ranks to show **"Deals You Can Use Right Now"**.

### Journey 2: "I'm About to Pay / Go Out" (High-Intent Search & Map)
- **Scenario A (Brand Search):** User is standing in front of *Apex* or *Chillox* or *Takeout*. Types the brand name -> sees a **Deal Comparison Card**:
  - *Best Deal:* **EBL Platinum Credit Card — 20% Off** (Min spend ৳1,000, Max ৳500)
  - *Alternative:* **bKash Payment — 10% Instant Cashback** (Up to ৳200/day)
  - *Alternative:* **GPStar Gold+ — 12% Off** (Show SMS code `APEX` to 29000)
- **Scenario B (Location Search):** User opens the **Near Me Map** in Dhanmondi / Banani / Uttara / Bashundhara City -> filters by `Dining` + `My Wallet Only` + `Valid Today` -> taps pin -> gets directions + exact redemption steps.

### Journey 3: Redemption & Verification Loop
- Every offer card must clearly display **5 non-negotiable fields**:
  1. **Headline Benefit** (e.g., `BOGO Buffet`, `Flat 20% Off`, `15% Cashback`)
  2. **Eligibility Badge** (e.g., `City Amex Gold`, `bKash App`, `Everyone`)
  3. **Exact Fine Print (Parsed cleanly, not a wall of text):** Min spend, max discount cap, valid days (e.g., *"Sun–Wed only"*), dine-in vs online.
  4. **How to Claim:** Copy promo code / Show SMS code / Pay via bKash QR / Redirect link.
  5. **Trust Bar:** `Verified 14h ago` • `👍 42 Works` • `👎 2 Expired` (One-tap feedback!).

### Journey 4: Smart Alerts & Seasonal Hubs
- **Watchlist Alerts:** *"Notify me when Aarong, Apex, or Star Tech has a new offer"* or *"Notify me when Cox's Bazar resorts have >30% off."*
- **Seasonal Mega-Hubs (Huge BD Traffic Spikes):** Dedicated curated hubs for **Ramadan Iftar/Sehri BOGO**, **Eid-ul-Fitr Fashion**, **Pohela Boishakh**, **11.11 / Black Friday**, and **Winter Clearance**.

---

## 3. Detailed Feature Roadmap

### Phase 1: MVP (Months 1–3) — *Validate Retention & SEO*
- **Platform:** SEO-optimized Web App (Next.js) + Mobile-first PWA (installable on Android) — or Web + Flutter Android MVP if budget allows.
- **Core Features:**
  - "My Wallet" selector (Banks, MFS, Telcos) — zero login friction.
  - Curated + semi-automated catalog of **1,500–3,000 verified offers** (Top 15 BD banks, bKash, Nagad, Rocket, Upay, GPStar, Robi Elite, Orange Club, top 100 Dhaka restaurants & clothing/grocery brands).
  - Smart Search supporting **English, Bangla, and Banglish** (e.g., *"bogo buffet gulshan"*, *"eid offer"*, *"ডিসকাউন্ট"*).
  - Area/Neighborhood filter (Dhaka zones + "Online/Nationwide").
  - "Works / Expired" 1-tap community feedback button.
  - WhatsApp / Messenger rich share cards (OG tags with clear discount graphics so sharing in friend groups drives viral traffic).
  - Internal Admin CMS for fast offer review, approval, and expiry management.

### Phase 2: Growth Engine (Months 4–9) — *Mobile Habit + Supply Scale*
- **Platform:** Native-feel **Android & iOS Apps** (Flutter).
- **Core Features:**
  - **Interactive "Near Me" Map** (PostGIS geo-queries + clustering).
  - **AI Social-Commerce Ingestion Pipeline:** Automated monitoring of 500–2,000 verified Bangladeshi brand/restaurant Facebook & Instagram pages -> Vision LLM extracts flyer offers -> human-in-the-loop quick approval.
  - **Merchant Self-Serve Portal (Free Tier):** Any verified restaurant, shop, or resort can submit their own offers, upload flyers, set start/end dates, and track views/clicks.
  - **User Accounts & Gamification:** Save/bookmark deals, custom deal alerts, "Deal Hunter" badges/leaderboards for users who submit or verify valid offers.
  - **Geo-fenced & Push Notifications:** Opt-in alerts for malls (Bashundhara City, Jamuna Future Park, Shimanto Shambhar) and favorite brands.

### Phase 3: Monetization & O2O Depth (Months 10–18) — *Revenue & Defensibility*
- **Merchant Ad Platform (Self-Serve):**
  - "Boost Offer" (pay via bKash/SSLCommerz — e.g., ৳500–৳3,000 for 7-day pinned placement in a neighborhood/category).
  - Category sponsorships (e.g., Ramadan Buffet Hub sponsored by a bank or MFS).
- **Exclusive App-Only Offers (QR/Code Redemption):**
  - Partner directly with 200+ Dhaka/Chattogram restaurants, cafes, salons, and boutiques for exclusive 10–25% off deals unlocked by showing a dynamic in-app redemption pass (solves attribution without POS integration!).
- **Affiliate Integration:**
  - Deep-link outbound clicks to Daraz, ShareTrip, GoZayaan, Agoda, Booking.com, Trip.com, and global SaaS/e-commerce partners.
- **Geographic Rollout:** Full offline coverage across Chattogram, Sylhet, Rajshahi, Khulna, Cox's Bazar, and Cumilla.

### Phase 4: Multi-Country Expansion (Months 18+)
- **Architecture-ready from Day 1** (see Section 4 below).
- **Target Wave 1 Markets:**
  - **Pakistan** (Karachi/Lahore/Islamabad — identical bank card BOGO + Easypaisa/JazzCash + Facebook SME dynamics).
  - **Sri Lanka** (Colombo — huge credit card dining/hotel discount culture).
  - **UAE / GCC** (Dubai/Riyadh — massive card & dining BOGO market with 10x higher ARPU/ad spend, though higher competition from The Entertainer/Cobone).

---

## 4. Designing for Multi-Country Expansion From Day 1

Even though you launch in Bangladesh only, retrofitting multi-country support later is painful. Build these **5 cheap abstractions on Day 1**:

1. **Country & Tenant Isolation (`country_code`):** Every `Offer`, `Merchant`, `Outlet`, `PaymentProvider` (Bank/MFS/Telco), and `City/Zone` carries an ISO `country_code` (`BD`, `PK`, `LK`, `AE`) and `currency_code` (`BDT`, `PKR`, `LKR`, `AED`).
2. **Modular Provider Registry:** Banks, MFS, and Telcos are data-driven entities—not hardcoded enums. Adding a new country means plugging in that country's provider registry and scraper configs.
3. **i18n & Multi-Script Search:** Store localized fields (`title_en`, `title_local`, `search_aliases`) so `en` + `bn` works in BD, and `en` + `ur` / `ar` / `id` drops in cleanly later.
4. **Timezone-Aware Expiry:** Store all `starts_at` / `ends_at` in UTC with explicit `timezone` (`Asia/Dhaka`), so flash deals expire accurately in each country.
5. **URL Structure for Global SEO:** Use country-prefixed or ccTLD-ready routing (e.g., `brand.com/bd/dhaka/dining` or `bd.brand.com`) so SEO authority scales cleanly when adding `/pk/` or `/ae/`.
