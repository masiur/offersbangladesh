# 08 — Critiques, Risks & Brutally Honest Mitigations

Every founder falls in love with their idea. Before committing time and money, here is the **red-team critique** of why centralized offer platforms historically fail—and specifically what can kill this product in Bangladesh.

---

## 1. The 10 Biggest Risks (Ranked by Lethality)

### Risk 1: The "Stale Offer" Trust Death Spiral *(Lethality: CRITICAL)*
- **The Critique:** You plan to cover restaurants, clothing stores, hotels, and shops. Maintaining accurate expiry dates, branch exclusions, and hidden T&Cs across 10,000+ offers is brutal. If a user tries **two** offers from your app and even **one** is expired or rejected by a cashier, they uninstall immediately and never return.
- **Mitigation:**
  - Start narrow (Dhaka + Top 15 Banks/MFS/Telcos) where data is structured and reliable.
  - Enforce aggressive **auto-expiry / soft-TTL** (better to show 500 100%-valid offers than 5,000 half-broken ones).
  - Implement the **3-strike Crowd Circuit-Breaker** (auto-hide offers flagged expired) and display transparent `"Verified X hours ago"` badges.

### Risk 2: The "Zero Loyalty / Coupon Chaser" Problem *(Lethality: HIGH)*
- **The Critique:** Deal hunters are inherently disloyal. Many users will Google `"Aarong offer today"`, land on your site, read the discount, close the tab, and never download your app. Why would they open *your* app weekly?
- **Mitigation:**
  - Make the app **personalized via "My Wallet"** (Google can't instantly filter every restaurant near you by *your exact combination* of City Amex + bKash + GPStar).
  - Build **push-alert habits** (Watchlists for favorite brands + Friday weekend deal digests + Mall geofencing).
  - Treat Google SEO Web as your free **top-of-funnel acquisition engine** that converts repeat visitors into app users.

### Risk 3: Bangladesh Bank PSP / Wallet Regulatory Trap *(Lethality: CRITICAL if ignored)*
- **The Critique:** If you market "Cashback" and store BDT balances inside an in-app wallet, you risk violating **Bangladesh Bank's Payment Systems Act / PSP regulations** (which strictly prohibit unauthorized closed-loop wallets/e-money). Additionally, if you sell prepaid deal vouchers directly, the **Digital Commerce Operational Guidelines 2021** require DBID registration and bank/PSP escrow compliance.
- **Mitigation:**
  - **Phase 1–2:** Position strictly as an **Offer Discovery & Aggregation Platform** (aggregate *existing* bKash/Nagad/bank cashbacks and store discounts—never hold user money).
  - Register a proper entity + **DBID (Digital Business Identification)** early.
  - If adding affiliate cashback payouts later, partner with a licensed MFS/PSP for direct instant disbursement (no stored balance) or consult a Bangladesh fintech lawyer before launching a wallet.

### Risk 4: Facebook / Meta Scraping Fragility & Legal Risk *(Lethality: HIGH)*
- **The Critique:** Relying on scraping Facebook pages for local SME deals is fragile—Meta aggressively blocks scrapers, changes DOMs weekly, and strictly forbids automated scraping in its Terms of Service.
- **Mitigation:**
  - Never depend 100% on unauthorized FB scraping.
  - Use **Institutional sources (Banks/MFS/Telcos)** for your base layer.
  - Transition SMEs to **Opt-In Ingestion**: Merchant Self-Serve Portal, **WhatsApp Business Flyer Bot**, or official Meta Graph API (merchants click "Connect my Facebook Page" to auto-sync their promo posts to your app for free!).
  - Supplement with community UGC submissions.

### Risk 5: The Chicken-and-Egg Marketplace Trap *(Lethality: HIGH)*
- **The Critique:** Merchants won't upload deals or pay for boosts unless you have thousands of active users. Users won't come unless you have great deals.
- **Mitigation:**
  - **Solved by the "Wallet-Aware" Wedge:** You do **not** need a single merchant to sign up on Day 1 to have 3,000+ high-value deals live (via Bank, MFS, and Telco partner directories). Build the user base first on aggregated public deals -> then monetize merchants once you have proven local traffic.

### Risk 6: Platform Risk from Super-Apps (bKash, Foodpanda, Pathao) *(Lethality: MEDIUM-HIGH)*
- **The Critique:** What stops bKash or Foodpanda from building a better offers directory?
- **Mitigation:**
  - **Structural Conflict of Interest protects you:** bKash will *never* promote Nagad's 20% cashback or City Bank Amex's BOGO buffet. Foodpanda will *never* promote dine-in deals at non-partner restaurants or clothing sales at Aarong. Your moat is **neutrality across all payment rails and categories**.

### Risk 7: Low Monetization / ARPU Ceiling in Bangladesh *(Lethality: MEDIUM-HIGH)*
- **The Critique:** Consumer willingness to pay for apps in Bangladesh is very low, digital ad CPMs are tiny ($0.50–$1), and SMEs are notoriously hard to convert into recurring SaaS/ad payers without field sales.
- **Mitigation:**
  - Focus on **high-margin B2B revenue** (Banks paying CPL for credit card applications, Ramadan/Eid brand hub sponsorships, and simple pay-as-you-go bKash "Boost Deal" packages rather than complex SaaS contracts).
  - Keep fixed overhead ultra-lean (automation + Vision AI instead of a 30-person manual data entry team).
  - Use Bangladesh as your **product & AI R&D lab**, then expand into higher-ARPU markets (e.g., UAE/GCC or SEA) once the engine is proven.

### Risk 8: Merchant Bypass & Cashier Ignorance *(Lethality: MEDIUM)*
- **The Critique:** In Bangladesh, even when a bank or brand officially announces a discount, branch cashiers often say *"Sir, our manager didn't inform us"* or *"POS machine isn't working for that card."*
- **Mitigation:**
  - Always attach **Official Source Proof** (link to bank/brand page or official promo image) inside the offer detail screen so the user can show it to the cashier.
  - Allow users to rate *"Redemption Experience"* per outlet so problematic branches get flagged.

### Risk 9: Fake Discounts ("Inflate Price 30%, Offer 25% Off") *(Lethality: MEDIUM)*
- **The Critique:** Many local e-commerce/retail "offers" in BD are fake markups before a "sale."
- **Mitigation:**
  - Prioritize **verifiable payment-rail discounts** (bank/MFS instant % off at checkout, which cannot easily be faked per-card) and let the **community upvote/downvote** deal quality (Slickdeals style) so fake deals sink to the bottom.

### Risk 10: Scope Creep ("Trying to Build Everything at Once") *(Lethality: HIGH)*
- **The Critique:** Trying to build Web + Android + iOS + Cashback Wallet + QR POS + 8 Verticals + International on Day 1 guarantees running out of money or burning out before finding Product-Market Fit.
- **Mitigation:**
  - Respect the **4-Week Validation Sprint** (Doc 02) and **Phased Roadmap** (Doc 04).

---

## 2. Final Strategic Verdict

| Dimension | Score (1–10) | Rationale |
| :--- | :---: | :--- |
| **Problem Reality (Pain)** | **8.5 / 10** | Offer fragmentation across 56 banks, 4 MFS, 3 telcos, and FB SMEs is genuinely painful in BD. |
| **Market Timing (2026)** | **8.5 / 10** | 52.9M cards, 240M MFS accounts, 137M internet users, and cheap Vision LLMs (for flyer parsing) make 2026 the ideal moment. |
| **Technical Feasibility** | **8.0 / 10** | Standard modern stack + Vision AI makes a lean MVP achievable in 6–10 weeks. |
| **Operational / Data Difficulty** | **4.0 / 10** *(Hard)* | Keeping offers fresh, accurate, and non-expired is a relentless daily operational challenge. |
| **Monetization Difficulty (BD)** | **5.5 / 10** *(Moderate)* | Hard to monetize consumers directly; viable via B2B boosts, bank leads, seasonal sponsorships, and travel affiliates. |

### Bottom Line Recommendation
**Proceed—but do NOT build a generic coupon directory.**
1. **Run the 4-Week Lean Validation Sprint first** (300 curated Dhaka offers + "My Wallet" filter + Meta ad & WhatsApp retention test).
2. **Win the "Wallet-Aware Offer Engine" wedge** for Dhaka's urban card/MFS/telco users (Dining + Clothing + Groceries).
3. **Invest heavily in your Data & Freshness Moat** (automated bank/MFS/telco scrapers + Vision LLM flyer parser + WhatsApp Merchant Bot + Crowd expiry flags).
4. **Build multi-country ready from Day 1**, so once the playbook is profitable in Bangladesh, you can replicate it into higher-ARPU markets.
