# Supplier-Quality-and-Performance-Analysis

![image alt](https://github.com/TemitopeHassan-Analyst/Supplier-Quality-and-Performance-Analysis/blob/7945b5e43f09ea4ae35a17467384876b93586e1e/Screenshot%202026-05-05%20012043.png)

## Introduction
The Supplier Quality and Performance Dashboard provides a comprehensive view of the organization’s supply chain health by tracking key metrics, including defect volume, downtime hours, and associated costs, across vendors, plants, and material types. It enables visibility into how supplier quality issues translate into operational disruptions and financial impact. By integrating defect classification, vendor performance, plant-location analysis, material types analysis, and temporal trends, the dashboard supports data-driven decision-making to improve product quality, reduce downtime, and optimize supplier relationships.

## Key Business Questions This Analysis Seeks to Answer
The dashboard is designed to help stakeholders move from raw data to decisions by addressing the following critical business questions:
1. Quality & Cost Impact
 - How are supplier defects impacting overall downtime and operational costs?
 - What is the trend of defects, downtime hours, and cost over time?
 - Are quality issues improving or deteriorating (MoM / YoY)?

2. Vendor Performance
 - Which vendors are contributing the most to downtime and defects?
 - Who are the highest-risk vs lowest-risk suppliers?
 - Are there vendors with high defects but low operational impact, and why?

3. Defect Severity & Classification
 - What proportion of defects are:
  - Impacting operations?
  - Not impacting operations?
  - Being rejected?
 - Are we focusing on the right types of defects to reduce downtime?

4. Plant-Level Vulnerability
 - Which plants experience the highest downtime due to supplier issues?
 - Are certain plants more sensitive to supplier quality problems?

6. Vendor–Plant Interaction
 - Which supplier–plant combinations create the highest risk?
 - Are poor-performing suppliers concentrated in specific plants?

## Data Cleaning and Transformation (Power Query)
To create the necessary data model for doing analysis and fulfilling the business needs defined in the business questions, the supplier dataset was further broken down into dimensions and fact tables. Also, a date table was created to support time intelligence analysis and was corrected in the data model in a later step of the process.

## Data Modelling
The dataset was structured using a star schema design inside the Power BI Data Model, enabling:

- Time intelligence analysis
- Relationship-based calculations
- Advanced measure creation
- Scalable performance reporting

![image alt](https://github.com/TemitopeHassan-Analyst/Supplier-Quality-and-Performance-Analysis/blob/238505c641a8c208d7d47fdae95cb74f9e507125/Screenshot%202026-04-14%20084929.png)

### Supplier Quality and Performance Dashboard
![image alt](https://github.com/TemitopeHassan-Analyst/Supplier-Quality-and-Performance-Analysis/blob/df86f345b9aee0ff46f42eb053f0c4e5e0c977ca/Screenshot%202026-05-04%20092737.png)

### Key Insights (Overview)
Key Performance Indicators
Defects: 2.31bn → very high scale problem
Downtime Hours: 192K
Downtime Cost: $1.92M
All three KPIs are up ~8% MoM and ~150% YoY → systemic deterioration, not noise

Trend Insight
Monthly trend shows:
- A dip mid-year (May–July) followed by a sharp spike (Aug–Oct)
- Indicates seasonality OR process breakdown introduced mid-year

Distribution of Defects
- No Impact: 39.54% (largest share)
- Impact: 32.22%
- Rejected: 28.23%
This indicates that a large portion of defects are not immediately causing downtime
But 60% (Impact + Rejected) are still operationally significant → major inefficiency

### Recommendations
- Shift focus from detection → prevention
- Investigate the Aug–Oct spike
- Reduce the 'No impact waste' by applying the defect Pareto (80/20) to eliminate recurring low-risk defects
