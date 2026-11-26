# Supply Chain Performance & OTIF Analytics Dashboard (AtliQ Mart)

## Project Overview
An end-to-end interactive Power BI dashboard built to analyse delivery service-level performance across **57,096 order lines**, **3 cities** (Surat, Ahmedabad, Vadodara), and **15 retail chains** for an FMCG distributor. The report diagnoses why On-Time In-Full (OTIF) delivery is missing contractual targets and pinpoints SKU-level inventory bottlenecks.

## Tech Stack & Data Model

* **Tools:** Microsoft Power BI (Desktop & Service), PostgreSQL (Neon Cloud), DAX, Power Query (M), Star Schema Data Modeling
* **Data Architecture:** Cloud-hosted 6-table Star Schema in **Neon PostgreSQL** (`aws-ap-southeast-1`) connecting `fact_orders_aggregate` and `fact_order_lines` with `dim_customers`, `dim_products`, `dim_date`, and `dim_targets_orders`
* **Cloud Automation:** Direct PostgreSQL connector in Power BI Service with scheduled daily refresh (9:00 AM IST) — zero local CSV dependencies or on-premises gateways
* **Custom DAX Measures (10 KPIs):** `OTIF %`, `OTIF Target %`, `On-Time %`, `On-Time Target %`, `In-Full %`, `In-Full Target %`, `LIFR %` (Line Item Fill Rate), `VOFR %` (Volume Order Fill Rate), `Total Orders`, and `Total Order Lines`

## Key Business Insights
* **Systemic OTIF Shortfall:** Overall **OTIF % is 29.02% against a 65.91% target** (a 36.9 percentage-point gap), pulled down primarily by incomplete orders (**52.78% In-Full %**) rather than transit delays (**59.03% On-Time %**).
* **Bulk Volume vs. SKU Stockouts:** **VOFR % reaches 96.59%** while **LIFR % sits at 65.96%** across Beverages, Dairy, and Food. Warehouses deliver nearly the entire ordered volume, but missing a few units on individual SKUs breaks complete order compliance.
* **Customer Churn Risk:** **Propel Mart** leads performance (~41% OTIF), whereas **Coolblue**, **Acclaimed Stores**, and **Lotus Mart** record **14%–16% OTIF** against 54%–58% targets, putting key contract renewals at risk.
* **Uniform Regional Performance:** All three cities hover within a narrow band—**Surat (30.07% OTIF)**, **Ahmedabad (29.33% OTIF)**, and **Vadodara (27.78% OTIF)**—confirming that inventory availability is a network-wide bottleneck rather than a city-specific logistics issue.

## Actionable Recommendations
1. **Priority Safety Stock:** Reallocate buffer inventory for high-velocity SKUs tied to high-risk accounts (**Coolblue**, **Acclaimed Stores**, and **Lotus Mart**).
2. **Pre-Dispatch LIFR Alerts:** Track **LIFR %** alongside **VOFR %** in weekly warehouse reviews so partial orders are flagged before dispatch.

## Repository Files
* `AtliQ_Supply_Chain_v2.pdf` — High-resolution static export of the executive dashboard for quick viewing.
* `AtliQ_Supply_Chain_v2.pbix` — Interactive Power BI Desktop file containing the data model, Power Query steps, and DAX formulas.
