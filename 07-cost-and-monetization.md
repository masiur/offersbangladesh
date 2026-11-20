# 07 — Cost Estimation, Monetization & Unit Economics

*(Exchange rate reference: ~1 USD ≈ ৳120 BDT. Figures reflect realistic 2026 Bangladesh & cloud pricing.)*

---

## 1. Initial Build Cost (MVP: Months 1–3)

Your build cost depends heavily on *who* builds it.

| Build Approach | Scope Covered (3 Months) | Estimated Cost (BDT) | Estimated Cost (USD) | Best For |
| :--- | :--- | :---: | :---: | :--- |
| **Option A: Solo Technical Founder / Indie** | Next.js Web + PWA, NestJS/Postgres/Meilisearch, Python scrapers + Gemini Flash pipeline, Admin CMS. (Flutter app in Month 4–5). | **৳1.5L – ৳3L** *(tools, domain, ads, part-time data intern)* | **$1,250 – $2,500** | Bootstrapped founder with coding skills. **Lowest risk.** |
| **Option B: Lean In-House Squad (BD)** | 1 Full-Stack Dev (৳80K/mo) + 1 Flutter Dev (৳70K/mo) + 1 Data/Ops Intern (৳20K/mo) + UI/UX Freelancer (৳60K one-off) for 3 months. | **৳6L – ৳8L** | **$5,000 – $6,700** | Funded founder wanting Web + Mobile Apps fast. |
| **Option C: Local Software Agency (BD)** | Turnkey Web + Android + iOS + Admin Panel + Basic Scrapers. | **৳15L – ৳30L+** | **$12,500 – $25,000+** | Non-technical founder. *(Warning: agencies rarely maintain scrapers/data pipelines well post-handoff!)* |

> **Recommendation:** Start with **Option A or a leaner Option B** (launch SEO Web + PWA first in 6–8 weeks, validate traction, then invest in Flutter apps).

---

## 2. Monthly Operating Cost Across 3 Growth Stages

### Stage 1: Launch / MVP (10,000 MAU • ~3,000 Active Offers)
| Cost Item | Monthly (USD) | Monthly (BDT) | Notes |
| :--- | :---: | :---: | :--- |
| Cloud Hosting (VPS/Managed Postgres + Redis + Meilisearch) | $40 – $70 | ৳4,800 – ৳8,400 | DigitalOcean/Hetzner/Railway Singapore |
| Cloudflare CDN + R2 Storage | $0 – $10 | ৳0 – ৳1,200 | Generous free tier |
| AI Extraction (Gemini Flash Vision for flyers/PDFs) | $10 – $25 | ৳1,200 – ৳3,000 | ~5,000–15,000 flyer parses/month |
| Scraping Proxies / Headless Browser | $15 – $30 | ৳1,800 – ৳3,600 | Lightweight rotating proxies |
| Maps / SMS OTP / Email / Apple & Play Store amortized | $15 – $30 | ৳1,800 – ৳3,600 | MapLibre/OSM keeps maps near $0 |
| **Subtotal Tech Infra** | **$80 – $165** | **৳9,600 – ৳19,800** | Very lean! |
| Part-Time Data/Content Moderator (1 person in BD) | $150 – $250 | ৳18,000 – ৳30,000 | Crucial for verifying offers & zero zombies |
| Marketing / Meta Ads Testing | $200 – $400 | ৳24,000 – ৳48,000 | Initial user acquisition |
| **Total Stage 1 Burn** | **$430 – $815/mo** | **৳51,600 – ৳97,800/mo** | |

### Stage 2: Growth (100,000 MAU • ~15,000 Active Offers)
| Cost Item | Monthly (USD) | Monthly (BDT) | Notes |
| :--- | :---: | :---: | :--- |
| Cloud Infra (Managed RDS/PostGIS, Redis, Meilisearch, API nodes) | $300 – $600 | ৳36,000 – ৳72,000 | Auto-scaling API + read replica |
| AI Pipeline + Proxies + SMS OTP + Monitoring | $150 – $300 | ৳18,000 – ৳36,000 | Higher volume flyer ingestion & user OTPs |
| Team (2 Devs + 2 Data/Ops + 1 B2B Merchant Sales/Growth) | $2,800 – $4,500 | ৳3.36L – ৳5.4L | Local BD salaries |
| Performance Marketing & Seasonal Campaigns | $1,000 – $2,000 | ৳1.2L – ৳2.4L | Eid/Ramadan/Campus pushes |
| **Total Stage 2 Burn** | **$4,250 – $7,400/mo** | **৳5.1L – ৳8.88L/mo** | |

### Stage 3: Scale (1,000,000 MAU • National + Expanding Regional)
- **Tech Infra + AI + Data:** $2,000 – $4,500/mo (৳2.4L – ৳5.4L)
- **Team (12–20 people across Eng, Data, Sales, Marketing):** $15,000 – $30,000/mo (৳18L – ৳36L)
- **Marketing & Partnerships:** $8,000 – $20,000/mo
- **Total Stage 3 Burn:** **$25,000 – $55,000/mo** (funded by revenue or Seed/Series A).

---

## 3. Monetization Models (Ranked by Viability in Bangladesh)

Not all global monetization models work in Bangladesh. Here is the realistic ranking:

### Rank 1: Merchant Self-Serve Boosts & Sponsored Placements *(Fastest Cashflow)*
- **How it works:** Listing regular offers is **100% free** (builds supply). Merchants pay via bKash/card to:
  - Pin their offer to the top of `"Dhanmondi Dining"` or `"Eid Clothing"` for 7 days (৳1,500 – ৳5,000).
  - Send a targeted geo-push notification to 5,000 nearby users (৳2,000 – ৳5,000).
  - Feature on the Home Banner during Ramadan/Eid/Pohela Boishakh (৳25,000 – ৳1,50,000/week).
- **Why it works in BD:** SMEs already burn ৳15K–৳1L/mo on Facebook boosts with low intent. Our audience has **10x higher buying intent**.

### Rank 2: Seasonal Brand & Financial Sponsorships *(Highest Margin)*
- **How it works:** Sell branded hubs to banks, MFS, and big brands:
  - *"Ramadan Iftar Buffet Hub — Powered by City Bank Amex"*
  - *"Eid Fashion Deals — Sponsored by bKash / Apex"*
  - **Card Acquisition Leads (CPL):** When a user sees an awesome EBL or BRAC Bank offer they don't own, show a CTA: *"Don't have an EBL Visa? Apply in 2 mins."* Banks pay **৳500 – ৳2,000 per qualified credit card lead**!

### Rank 3: Affiliate Commissions (Online & Travel) *(Passive Scale)*
- **How it works:** Earn 2%–8% commission on outbound purchases via Daraz Affiliate, ShareTrip, GoZayaan, Agoda, Booking.com, Trip.com, and global SaaS/hosting tools.
- **Reality check:** Travel (flights/hotels) and international bookings pay far better than local grocery/retail affiliates.

### Rank 4: Exclusive Paid Vouchers / Membership Pass *(Phase 3 — The Entertainer Model)*
- **How it works:** Once you have 200+ exclusive merchant deals (e.g., BOGO main courses, 30% off resorts), charge users **৳499 – ৳999/year** for a "Pro Saver Pass"—or sell it **B2B** to corporates/banks as an employee/customer perk.
- **Warning:** Do **not** paywall basic aggregated deals! Only paywall *exclusive* high-value deals where 1 redemption pays back the annual fee.

### Rank 5: Display Ads (Google AdSense / Programmatic) *(Fallback Only)*
- **Reality check:** Bangladesh display CPMs are notoriously low ($0.30–$1.20 per 1,000 views). Programmatic ads also clutter the UI and ruin trust. Use sparingly on SEO blog/event pages only.

### What to AVOID Early: "Direct Cashback Wallet"
- Operating a ShopBack-style wallet where you hold users' cashback balances in BDT triggers **Bangladesh Bank PSP/e-wallet licensing rules**, creates customer support nightmares over failed tracking, and burns working capital. Avoid until scale/licensing.

---

## 4. Break-Even Scenario (Stage 2 Target: 100K MAU)

Can this business reach profitability cleanly in Bangladesh without huge VC funding? **Yes, if kept lean:**

| Revenue Stream (at 100K MAU) | Conservative Monthly Estimate |
| :--- | :---: |
| 60 SMEs buying Featured Boosts (avg ৳4,000/mo) | ৳2,40,000 ($2,000) |
| 2 Bank / Brand Seasonal Sponsorships or Hub Banners | ৳2,50,000 ($2,083) |
| 150 Credit Card / Financial Leads (avg ৳800 CPL) | ৳1,20,000 ($1,000) |
| Affiliate Commissions (Daraz + Hotels/Travel) | ৳1,50,000 ($1,250) |
| **Total Monthly Revenue** | **৳7,60,000 (~$6,333/mo)** |

**Verdict:** At **~100K–150K MAU**, a lean Bangladesh team (Stage 2 burn: ৳5.1L–৳8.8L/mo) can hit **ramen profitability / break-even**, with massive seasonal spikes during **Ramadan/Eid (March–June)** and **Winter/11.11 (Nov–Jan)** generating 40–50% of annual profits.
