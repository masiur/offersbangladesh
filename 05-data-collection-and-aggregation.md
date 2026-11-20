# 05 — Data Collection, Aggregation & Freshness Challenges

> **Critical Truth:** In an offers platform, **software is 20% of the challenge; data accuracy and freshness are 80%.** If a user walks into a restaurant because your app promised "20% off with EBL Visa" and the waiter says *"That ended last month,"* you lose that user permanently.

This document breaks down the **5-Pillar Data Engine** needed specifically for Bangladesh.

---

## 1. The Unique Data Reality of Bangladesh

Unlike the US or Europe (where affiliate networks like CJ, Rakuten, Impact, and structured APIs feed 80% of coupon sites), Bangladesh's offer data is **wildly unstructured**:
1. **Banks** publish offers as HTML tables, pagination-heavy microsites, or **unstructured PDFs** (often updated quarterly or seasonally for Ramadan/Eid).
2. **MFS (bKash, Nagad, Upay)** publish campaign pages with complex caps (*"10% cashback up to ৳100/day, max ৳300/campaign, min ৳500 spend"*), often buried inside promo images.
3. **Telcos (GPStar, Robi Elite, Orange Club)** publish partner directories split across tiers (Silver/Gold/Platinum/Signature).
4. **70%+ of Local SMEs** (restaurants, cafes, boutiques, resorts) **do not even have a website**—they post a graphic flyer on their **Facebook Page** with text like *"Flat 25% Off on all platters till 30th Nov! Valid at Dhanmondi & Uttara branches only."*

---

## 2. The 5-Pillar Data Ingestion Architecture

No single data source is enough. You need a hybrid pipeline combining automated scrapers, Vision AI, merchant direct input, affiliates, and community verification.

### Pillar 1: Structured Institutional Scrapers (Banks, MFS, Telcos) — *Launch Core*
- **Targets:** Top 15 BD Banks (City Bank, EBL, BRAC, SCB, DBBL, MTB, Prime, UCB, Bank Asia, Pubali, Islami Bank, Eastern, Southeast, Trust, LankaBangla), 4 MFS (bKash, Nagad, Rocket, Upay), 3 Telcos (GPStar, Robi Elite, Orange Club).
- **How it works:**
  - Scheduled Playwright / Python scrapers (daily for MFS/campaign pages, weekly for bank partner directories).
  - PDF parser (`pdfplumber` / LLM extraction) for banks that upload PDF merchant lists.
  - Change-detection hashing (only re-process pages whose DOM/PDF hash changed, saving compute & AI tokens).
- **Volume:** Easily yields **3,000–8,000 structured offers** with very high reliability.

### Pillar 2: AI Social-Commerce Flyer Radar (Facebook / Instagram) — *Bangladesh Moat*
- **The Problem:** Local clothing stores, restaurants, and Cox's Bazar resorts announce flash sales via image flyers on Facebook/Instagram.
- **How it works:**
  1. Maintain a curated watchlist of **500–3,000 official brand/restaurant pages** (starting with Dhaka's top brands & restaurants).
  2. Ingest public page posts/flyers via compliant third-party social data providers, official Meta Graph API (for onboarded merchants who connect their page), or human-assisted bookmarklet/extension tools for moderators. *(Warning: direct aggressive scraping of Facebook violates Meta ToS and breaks constantly—see Legal/Risk section in Doc 08.)*
  3. **Vision LLM Extraction (e.g., Gemini 2.5 Flash):** Pass the post caption + flyer image to a multimodal LLM with a strict JSON schema:
     ```json
     {
       "merchant_name": "Kacchi Bhai",
       "discount_type": "PERCENTAGE",
       "discount_value": 15,
       "payment_method": "bKash",
       "min_spend_bdt": 500,
       "max_cap_bdt": 150,
       "valid_branches": ["Dhanmondi", "Mirpur", "Uttara"],
       "starts_at": "2026-11-20",
       "ends_at": "2026-11-30",
       "confidence_score": 0.94
     }
     ```
  4. **Confidence Routing:**
     - Confidence >= 0.90 from a whitelisted brand -> Auto-publish (flagged "AI-Parsed").
     - Confidence 0.70–0.89 -> Route to a **1-click Human Review Queue** (1 junior ops moderator can approve 200–300 pre-parsed deals/hour!).
     - Confidence < 0.70 -> Discard (not a real offer, just a regular marketing post).

### Pillar 3: Merchant Direct Self-Serve Portal — *Long-Term Scalability*
- **How it works:** Give restaurants, clothing shops, and hotels a dead-simple **WhatsApp-like or Mobile Web Merchant Portal** where they can:
  - Upload a promo flyer (our Vision AI auto-fills the form for them so they don't have to type!).
  - Pick branches, validity dates, and redemption rules.
  - Get a **"Merchant Verified ✓"** badge (ranked higher in search).
- **Pro Tip for BD:** Many SME owners won't log into a web dashboard. Build a **WhatsApp Business Bot** where a verified merchant simply forwards their promo flyer to your WhatsApp number -> AI parses it -> bot replies *"Publish '20% off till Nov 30'?"* -> Merchant taps `[Yes]` -> Live in 10 seconds!

### Pillar 4: Affiliate & E-Commerce Feeds
- **Targets:** Daraz Affiliate API/portal, ShareTrip, GoZayaan, Agoda, Booking.com, Trip.com, CJ/Impact/Admitad (for global software/hosting/travel deals relevant to Bangladeshi freelancers & travelers).
- **Value:** Auto-updated promo codes + direct monetization.

### Pillar 5: Crowdsourced UGC (User-Submitted Deals & Flags)
- **How it works:** Users snap a photo of a **storefront standee / mall banner** (e.g., *"Flat 40% Off at Bata Bashundhara City"*) or paste a promo code.
- **Incentive:** Gamified points, "Top Deal Hunter" badges, and monthly micro-rewards (e.g., mobile recharge or food vouchers for top verified contributors).
- **Spam Control:** New users' submissions go through moderation; trusted high-reputation users auto-publish.

---

## 3. The 4 Hardest Data Engineering Problems (and How to Solve Them)

### Problem 1: Entity Resolution & Deduplication
- **The Mess:** Bank A lists `"The Westin Dhaka - Seasonal Tastes"`, Bank B lists `"Seasonal Tastes (Westin)"`, and bKash lists `"Westin Hotel Gulshan"`.
- **The Fix:** Maintain a **Canonical Merchant & Outlet Registry** (`merchants` -> `outlets` with Google Place ID / lat-lng coordinates + alias table). During ingestion, use fuzzy matching + vector embeddings to map incoming raw merchant names to canonical `merchant_id` / `outlet_id`. This unlocks the killer feature: **comparing 5 different bank/MFS offers on one unified merchant page**.

### Problem 2: Offer Expiration & "Zombie Deals"
- **The Mess:** Many Bangladeshi offers don't state an end date (*"Limited time offer!"* or *"Till stock lasts"*).
- **The Fix — Multi-Layer Freshness Engine:**
  1. **Hard TTL:** Offers with explicit `ends_at` auto-archive at midnight `Asia/Dhaka`.
  2. **Soft TTL (Decay):** Offers *without* an end date get a default 14-day (dining/retail) or 30-day (bank ongoing) decay timer. Before expiring, the system either re-checks the source URL or prompts the merchant/ops queue.
  3. **Crowd Circuit-Breaker:** If **3+ unique users** tap *"Expired / Didn't Work"* within 48 hours (weighted by user trust score), the offer is immediately **soft-hidden** and pushed to the verification queue.
  4. **Visible Trust Score:** Display `"Verified by Merchant"`, `"Verified from Bank Site (2d ago)"`, or `"Community Reported"` so user expectations match reality.

### Problem 3: Fine Print & Complex Conditions
- **The Mess:** `"Up to 50% off"` in Bangladesh often means *"50% off on one obscure item, 10% on everything else"* or *"Only on Tuesdays between 12–3 PM for Signature Credit Cards, max cap ৳300."*
- **The Fix:** Enforce structured metadata fields (`min_spend`, `max_discount_cap`, `valid_days_of_week`, `eligible_card_tiers`, `dine_in_only`, `up_to_flag`). Surface hidden caps clearly on the card so users trust your transparency over misleading ads.

### Problem 4: Multi-Branch Geo-Mapping
- **The Mess:** A brand like *Apex* or *Shwapno* has 200+ branches, while a restaurant offer might only apply to *"Dhanmondi & Banani outlets, excluding Uttara."*
- **The Fix:** Model `Offer <-> Outlet` as a flexible relationship: `applies_to_all_outlets: boolean` + optional `included_outlet_ids[]` / `excluded_outlet_ids[]`. Index all outlet coordinates in **PostGIS** so "Near Me" queries accurately reflect only offers valid at *that specific branch*.
