# Digital Traffic & Conversion Analytics (GA4 + Paid Media Integration)

![Looker Studio](https://img.shields.io/badge/Looker_Studio-4285F4?style=for-the-badge&logo=google&logoColor=white)
![Google Analytics 4](https://img.shields.io/badge/GA4-E37400?style=for-the-badge&logo=googleanalytics&logoColor=white)
![Google Sheets](https://img.shields.io/badge/Google_Sheets-34A853?style=for-the-badge&logo=googlesheets&logoColor=white)

## 📌 Executive Summary (BLUF)
This project solves a critical limitation in native **Google Analytics 4 (GA4)**: GA4 tracks on-site traffic and revenue, but lacks cost context for non-Google paid channels (Meta, TikTok). 

By blending GA4 web performance data with ad spend logs across channels, this dashboard unifies cross-channel **CPA (Cost Per Acquisition)** and **ROAS (Return on Ad Spend)** into a single executive dashboard to drive weekly media budget reallocation decisions.

* **Live Interactive Dashboard:** [Insert Your Looker Studio Share Link Here]
* **Target Region:** Australian E-Commerce Market

---

## 📊 Business Problem & Core Objectives
1. **Unify Spend & Traffic:** Eliminate isolated platform reporting by joining Meta and TikTok spend with GA4 event analytics.
2. **Evaluate Channel Efficiency:** Shift focus from vanity metrics (Clicks, Sessions) to efficiency metrics (**CPA**, **ROAS**, **CVR**).
3. **Budget Optimization:** Identify low-performing channels draining budget and reallocate capital to high-margin acquisition engines.

---

## 🛠 Data Architecture & Blending Logic

Two datasets were integrated using a **LEFT OUTER JOIN** inside Looker Studio to preserve ad spend records even on days with zero down-funnel conversions.

### Data Join Schema
```text
[ ad_spend_raw ] (Left Table)                 [ ga4_traffic_raw ] (Right Table)
──────────────────────────────                 ─────────────────────────────────
• date               (Join Key)  <=========>   • date               (Join Key)
• source_medium      (Join Key)  <=========>   • source_medium      (Join Key)
• campaign                                     • campaign
• ad_spend                                     • sessions
• impressions                                  • engaged_sessions
• clicks                                       • key_events
                                               • purchase_revenue
