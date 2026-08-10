# AdVantage Marketing — Campaign Performance Dashboard

A Power BI dashboard analyzing multi-channel ad campaign performance for a fictional marketing agency (AdVantage), tracking spend, funnel efficiency, and return on ad spend across 6 advertising channels — built from a raw, intentionally messy dataset to simulate a real-world analytics workflow.

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-blue?style=flat)
![Status](https://img.shields.io/badge/status-complete-brightgreen)

---

## Project Overview

AdVantage Marketing runs paid ad campaigns across 6 channels (Facebook, Google, Instagram, Email, LinkedIn, TikTok). Raw performance data existed, but spend, clicks, and revenue had never been connected into a single efficiency picture. This project answers the core question every marketing budget owner asks: **is the ad spend actually working, and if not, where should it move?**

## Business Questions Answered

- Out of everyone who sees an ad, how many click, and how many of those convert?
- Which channel delivers the best return for every dollar spent (ROAS)?
- Is any channel spending money without delivering proportional value?
- Where in the funnel is the biggest drop-off happening?

## Key Findings

| Metric | Result |
|---|---|
| Total Impressions | ~11.6M |
| Total Clicks | ~460K |
| Total Conversions | ~24K |
| Click-Through Rate (CTR) | ~4% |
| Conversion Rate | ~5% |
| Total Spend | ~$495,280 |
| Total Revenue | ~$2.2M |
| Return on Ad Spend (ROAS) | 4.45x |

- **Google Ads delivers the highest ROAS of all 6 channels**
- **LinkedIn Ads trails behind despite receiving comparable spend** — a direct signal that reallocating budget toward Google Ads could improve overall efficiency
- Cost per click averages **$1.08**, but jumps to **$21.05 per actual conversion** — illustrating how much harder it is to convert a click into a sale than to earn the click itself

This insight — pairing a specific underperforming channel with a specific recommended action — is the dashboard's central takeaway, designed to be immediately usable by a marketing budget owner.

## Dashboard Preview

The final report includes:
- 5 KPI cards (Spend, Revenue, ROAS, Conversion Rate, CTR)
- Funnel chart: Impressions → Clicks → Conversions
- Return on Ad Spend (ROAS) by channel (bar chart)
- Spend vs Revenue by channel (combo chart)
- Interactive slicers: Channel, Campaign Type, Device, Region

*(Add a screenshot of your finished dashboard here — drag the exported PNG/PDF into this repo and reference it, e.g. `![Dashboard Screenshot](screenshots/dashboard.png)`)*

## Data Source

The dataset is a synthetically generated, intentionally messy export (`AdVantage_Marketing_RAW.xlsx`) simulating real-world data quality issues:

- Inconsistent channel naming (e.g., "Facebook Ads" / "facebook ads" / "FB Ads")
- Spend stored as text with currency symbols mixed with clean numbers
- Conversions column mixing "N/A" text values with numeric data
- Rows where Clicks exceed Impressions — a genuinely impossible tracking glitch requiring a deliberate data-quality decision rather than a simple fix
- Duplicate and blank rows

## Tools & Skills Used

- **Power Query** — data cleaning, standardizing text, fixing data types, flagging data-quality issues
- **DAX** — SUM, DIVIDE, funnel-stage rate calculations, CALCULATE
- **Data Modeling** — star schema design (fact + dimension tables), relationship management
- **Power BI Desktop** — funnel visualization, report design, interactive slicers

## Data Model

**Fact table:** `Campaign Export` — one row per campaign-day record
**Dimension tables:**
- `Channels` — unique advertising channels, connected 1-to-many to Campaign Export
- `Calendar` — a generated date table (not extracted from raw data) ensuring a complete, unbroken date range for accurate time-based analysis

```
Channels (1) ──────< Campaign Export >────── (1) Calendar
```

## Key DAX Measures

```dax
Click-Through Rate (CTR) = 
DIVIDE([Total Clicks], [Total Impressions], 0)

Conversion Rate = 
DIVIDE([Total Conversions], [Total Clicks], 0)

Cost Per Conversion (CPA) = 
DIVIDE([Total Spend], [Total Conversions], 0)

Return on Ad Spend (ROAS) = 
DIVIDE([Total Revenue], [Total Spend], 0)
```

**Note on funnel-stage measures:** CTR and Conversion Rate deliberately use *different* denominators — CTR divides by Impressions, Conversion Rate divides by Clicks — because each stage's rate is calculated relative to the stage before it, not the very top of the funnel every time. This mirrors how a real marketing funnel narrows step by step.

## Data Cleaning Highlights

- Standardized inconsistent Channel, Device, and Region text values into clean categories
- Converted Spend from mixed text/currency format into a usable Decimal Number
- Fixed a text value ("N/A") mixed into the numeric Conversions column
- Investigated rows where Clicks exceeded Impressions — flagged them with a `Data Quality Flag` column instead of deleting them outright, preserving valid Spend/Revenue data while excluding them from CTR-specific analysis
- Sequenced blank-row removal *before* adding custom columns, to avoid custom-column text making blank rows undetectable

## Repository Contents

```
├── AdVantage_Marketing_RAW.xlsx         # Raw, messy source dataset
├── AdVantage_Marketing_Dashboard.pbix   # Power BI report file
├── AdVantage_Marketing_Dashboard.pdf    # Static PDF export of the dashboard
├── screenshots/                         # Dashboard preview images
└── README.md                            # This file
```

## How to Use

1. Clone or download this repository
2. Open `AdVantage_Marketing_Dashboard.pbix` in [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free)
3. Use the slicers (Channel, Campaign Type, Device, Region) to explore the data interactively
4. Refresh the data connection if using the raw `.xlsx` file with updated data

## About This Project

This project was built as part of a portfolio demonstrating end-to-end BI analyst skills: taking raw, imperfect data through cleaning, modeling, calculation, and visualization to a finished, decision-ready dashboard — mirroring the kind of ambiguous, real-world data a Data/BI Analyst encounters on the job.

---

**Author:** Aryan Mantrawadi
**Connect:** [LinkedIn](#) · [Portfolio](#)
