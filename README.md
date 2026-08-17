# Customer Churn Analysis Dashboard (Power BI)

## Executive Summary

This project presents a five-page Power BI dashboard analyzing customer churn for **Databel**, a fictitious telecom provider. The report brings together account, billing, service-usage, and support-interaction data into a single interactive tool for identifying who is churning, why, and where the business should focus retention efforts.

The dashboard moves from a high-level churn overview into focused pages on customer age, contracts and payment behavior, extra charges, and cross-cutting churn drivers.

## Business Problem

Customer churn directly erodes recurring revenue, and the drivers behind it are usually scattered across contract data, billing data, and support-call logs. The goal of this project was to build a single report that consolidates these sources so that retention, billing, and customer support teams can see churn rate, churn reasons, and the customer segments most at risk without cross-referencing separate exports.

## Dashboard Pages

### 1. Overview
High-level snapshot of churn across the customer base:
- KPI cards — Churn Rate, Number of Churned Customers, Total Number of Customers
- Top 5 Churn Reasons
- Churn by Category
- Customers by Contract Type (donut)
- Geographic map of churn by state

> **Insight:** Competitor offers are the #1 churn driver — 45% of the "category" split and 17% of individual reasons.

### 2. Age Groups
Explores how churn and spend vary across customer age bands:
- Total Number of Customers and Churn Rate by Age
- Average Monthly Charge and Churn Rate by Shared Plan/Group Size
- Account Length (in months) slicer

> **Insight:** Churn rate nearly doubles for customers over age 60.

### 3. Payment and Contract
Analyzes how contract type and payment method relate to churn:
- KPI cards — Avg. Customer Service Calls, Total Customer Service Calls
- Churn Rate by Average Account Lifetime and Contract Type (scatter)
- Churn Rate throughout Account Lifetime and Contract Type (line)
- Slicers — Contract Category, Payment Method
- Payment method distribution (pie)
- Play-axis button to step through payment methods

> **Insight:** Month-to-month churn (~45%) is far higher than any annual contract, and customers with more service calls are more likely to be on month-to-month plans.

### 4. Extra Charges
Looks at how data usage and add-on charges relate to churn:
- Churn Rate by Data Usage and Plan Type
- KPI cards — Avg. Extra International Charges, Avg. Extra Data Charges

> **Insight:** Unlimited-plan customers who use under 5 GB churn 3x more than customers without the unlimited plan.

### 5. Insights
Cross-cutting view tying customer support activity to churn outcomes:
- KPI cards — Total & Avg. Customer Service Calls, Avg. Extra International Charges, Avg. Extra Data Charges
- Average Customer Service Calls: Churned vs. Not Churned
- Top 5 States by Avg. Service Calls, by Churn Status
- Geographic map

> **Insight:** Churned customers make 6x more service calls than retained customers.

## Methodology

1. Sourced and cleaned the Databel customer dataset (accounts, billing, contracts, service usage, and support-call history) using Power Query.
2. Built a semantic model on the core customer table, with a dedicated measures table (`_Measures`) to keep DAX logic separate from raw data.
3. Created reusable DAX measures for churn rate, average customer service calls, and average extra data/international charges.
4. Designed five report pages, each focused on a specific angle of churn: overall performance, age demographics, contracts & payment, extra charges, and cross-cutting service insights.
5. Added slicers (contract category, payment method, account length) and a play-axis control for interactive, self-service exploration.
6. Surfaced the key takeaway from each page directly on the canvas as a callout, so business users get the "so what" without digging through the visuals.

## Skills

**Power Query:** data cleaning, shaping raw customer/billing/support data for analysis

**DAX:** CALCULATE, DIVIDE, SUM, COUNTNONNULL, and other aggregation/ratio measures for churn rate and service metrics

**Data Modelling:** dedicated measures table, KPI card design, slicer and play-axis interactivity

**Data Visualization:** combo charts, scatter plots, geographic maps, and clustered bar/column charts for churn segmentation

## Data Model

The report is built on a core **customer table** (`Databel - Data`), containing account, contract, billing, and support-call fields such as:

- Churn Label / Churn Category / Churn Reason
- Contract Type / Contract Category
- Payment Method
- Monthly Charge
- Account Length (in months)
- Customer Service Calls
- Age (bins) / State
- Unlimited Data Plan / Grouped Consumption

A separate **`_Measures`** table holds the DAX measures used across the report (e.g., Avg. Customer Service Calls, Avg. Extra Data Charges, Avg. Extra International Charges), keeping calculation logic cleanly separated from the raw data table.

## Key Insights

- **Competitor offers drive churn most** — the #1 reason customers leave, accounting for 45% of the churn-category split.
- **Age matters** — churn rate nearly doubles for customers over 60 compared to younger segments.
- **Contract type is a strong churn signal** — month-to-month customers churn at ~45%, well above any annual contract, and tend to place more service calls.
- **Usage mismatch drives churn** — unlimited-plan customers using under 5 GB churn 3x more often than customers without the unlimited plan, suggesting they're paying for a plan that doesn't fit their usage.
- **Support calls are a leading indicator** — churned customers made 6x more customer service calls than retained customers before leaving.

## Next Steps

1. Layer in a retention-cost or customer lifetime value (CLV) measure to prioritize which churn segments are worth targeting first.
2. Add drillthrough from the Overview page into a customer-level detail page for support teams handling at-risk accounts.

---

*Built in Power BI Desktop as a portfolio project analyzing a fictitious telecom company's customer churn.*
