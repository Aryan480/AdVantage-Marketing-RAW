# AdVantage Marketing — Campaign Performance Dashboard

## Overview
A Power BI dashboard analyzing multi-channel ad spend, funnel performance, and return on ad spend (ROAS) for AdVantage Marketing's 2024 campaigns.

## Purpose
Marketing leadership needed a single view to compare how budget was being spent across channels (Google, Facebook, Instagram, LinkedIn, TikTok, Email) versus the revenue and ROAS each channel actually generated, in order to make data-driven budget reallocation decisions.

## What I Did
- Modeled the raw campaign data (`AdVantage_Marketing_RAW.xlsx`) covering spend, revenue, impressions, clicks, and conversions by channel, campaign type, device, and region.
- Built slicers for **Channel**, **Campaign Type**, **Device**, and **Region** for flexible drill-down.
- Built KPI cards for Total Spend, Total Revenue, ROAS, Conversion Rate, and Click-Through Rate (CTR).
- Created a funnel visual (Impressions → Clicks → Conversions) to show drop-off through the marketing funnel.
- Built comparison charts for ROAS by channel and Spend vs. Revenue by channel.
- Documented the approach in `AdVantage_Marketing_Solution_Guide.pdf`.

## Outcome / Key Insights
- **$495.28K** total spend generated **$2.20M** in revenue, an overall ROAS of **4.45x**.
- Funnel: **11.65M** impressions → **460K** clicks → **24K** conversions (5% conversion rate, 4% CTR).
- **Google Ads** delivers the highest ROAS of all channels, while **LinkedIn Ads** trails behind despite comparable spend.
- This gap suggests reallocating budget away from LinkedIn Ads toward Google Ads could improve overall campaign efficiency.

## Files
| File | Description |
|---|---|
| `AdVantage_Marketing.pbix` | Power BI project file (data model, DAX measures, report) |
| `AdVantage_Marketing_RAW.xlsx` | Raw source data |
| `AdVantage_Marketing_Dashboard.pdf` | Exported PDF version of the report |
| `AdVantage_Marketing_Solution_Guide.pdf` | Write-up of the approach and solution steps |

## Tools Used
Power BI Desktop, DAX, Power Query

---
*Prepared by Aryan Mantrawadi — August 2026*
