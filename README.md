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

Worse Vendor performers

- Meetz also ranks #1 for downtime hours in the vendor performance table (755.3 hrs in worse-performers). Combined with its top rank in downtime hours, it is the single highest-risk vendor.
- Abata has the highest defect impact dollar cost ($1.93M from Raw Materials alone at $1,825.67/hr) — far exceeding all other vendor-material combinations.

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

### Vendor Performance

![image alt](https://github.com/TemitopeHassan-Analyst/Supplier-Quality-and-Performance-Analysis/blob/3bd30ef4929c4494135afe08adbee05d521bd946/Screenshot%202026-05-05%20035145.png)

### Key Insights
Top Downtime Contributors
Vendors like:
- Meejo (~1073 hrs)
- Realinks (~1059 hrs)
- Izio (~1039 hrs)

These vendors alone contribute a disproportionate share of downtime

Scatter Plot Insight (Defect Impact vs Downtime)
High-risk vendors:
- High defects + high downtime → critical suppliers
Medium-risk vendors:
- Moderate clustering → process inconsistency
Low-risk vendors:
- Scattered, low-density → stable

### Recommendation
| Tier              | Criteria                     | Action                       |
| ----------------- | ---------------------------- | ---------------------------- |
| 🔴 Strategic Risk | High downtime + high defects | Immediate escalation, audits |
| 🟡 Watchlist      | High defects OR downtime     | Performance improvement plan |
| 🟢 Stable         | Low both                     | Maintain, benchmark          |


2. Target top 5 vendors (not all)
- Likely top 20% vendors → 80% downtime
For each:
- Root cause analysis (RCA)
- Process capability review (Cp, Cpk)


3. Fix mismatch: high defects but low downtime
These are hidden cost drivers. Improve:
- Specification clarity
- Tolerance alignment
- Inspection automation

## Plant Performance

![image alt](https://github.com/TemitopeHassan-Analyst/Supplier-Quality-and-Performance-Analysis/blob/df2eb47439ac8e6a3bb1bd2ecf29dc79d63ecc2b/Screenshot%202026-05-04%20093126.png)

## Key Insights
Top Downtime Plants
- Garwood (6.0K hrs)
- Chatham (5.9K hrs)
- Waldoboro (5.7K hrs)

These plants are most vulnerable to supplier quality issues
- Charles City ranks #1 in "Worse Performers by Plant" with 7,506.7 downtime hours — the single highest-risk plant-level concentration.

🌍 Geographic Insight
The map suggests clustered plant issues
Could indicate:
- Regional supplier problems
- Logistics/handling issues

## Recommendation
1. Standardize quality thresholds
Different plants may be:
- Accepting/rejecting inconsistently
Implement:
- Global defect classification standard

2. Align vendors to plants strategically
- High-risk suppliers → avoid assigning to:
- High-throughput / critical plants

3. Strengthen incoming inspection at top plants
Focus on:
- Garwood, Chatham, Waldoboro

## Material Type Performance
![image alt](https://github.com/TemitopeHassan-Analyst/Supplier-Quality-and-Performance-Analysis/blob/621dd54ca0216945fe66b2392382f52493cb61a7/Screenshot%202026-05-04%20093143.png)


1. Defect Trends by Material Type
- Raw Materials and Corrugate are the top contributors to defects, accounting for ~0.56bn and 0.53bn defect quantities, respectively.
- Film, Labels, and Carton have significantly lower defect quantities (below 0.2bn each), suggesting these materials have relatively stable quality performance.
Interpretation:
- Supplier or process variability for raw materials and corrugate is likely driving higher rework, scrap, and production downtime.

2. Defect Causes
- Top defect causes: Bad Seams (146M), Miscellaneous Issues (114M), and Not Certified (106M).
- Foreign Material (80M) and Warped (66M) defects also indicate possible supplier handling or packaging weaknesses.
Interpretation:
- High “Bad Seams” and “Not Certified” rates suggest a mix of operator error, supplier QA gaps, or material incompatibility with manufacturing equipment.

3. Defect Quantity by Category
- Mechanicals (0.71bn) and Logistics (0.62bn) dominate defect impact.
- Materials & Components sit lower but may still drive accumulated losses through the value chain.
Interpretation:
- Defects are not purely material-based — they may stem from mechanical alignment issues or poor inbound logistics handling, emphasizing the need for joint supplier-process analysis.

## Recommendation
1. Cross-functional Root Cause Reviews:
- Jointly analyze Bad Seams and Foreign Material issues involving production, maintenance, and supplier engineering.
2. Automation/Inspection Investment:
- Introduce inline seam-detection systems and material vision inspection to catch defects early, reducing rework.
3. Certification Controls:
Tighten certification verification on incoming materials to curb the “Not Certified” defect category.

## Downtime Impact
![image alt](https://github.com/TemitopeHassan-Analyst/Supplier-Quality-and-Performance-Analysis/blob/413fdf6ec20418f73956bd2c57101efffafe6d40/Screenshot%202026-05-05%20070607.png)


## Key Insights
- Peak downtime cost/hour is between $217K–$243K in September to November, suggesting compounding issues during high production months.
- Weekdays, Tuesday–Thursday, have consistently higher downtime costs than weekends.
Interpretation:
- Downtime costs might align with full production utilization mid-week, when line loads and defect-processing times are longest.
Vendor vs. Plant Impact
- Vendors like Skiptube (Charlevoix) and Innojarn (Garwood) show high downtime cost/hr ($226–$597).
- Plants such as Bruce Crossing and Chatham show elevated defect counts, making them hotspots for process-quality investigations.
Vendor vs. Material Impact
- Vendor Abata appears multiple times with different materials and significant downtime costs/hour (up to $1,825.67/hr for Raw Materials and $789.17/hr for Controllers).
- This signals that Abata’s material quality directly correlates with high-cost production interruptions.

## Recommendations
1. Contract Leverage:
- Introduce performance-based payment adjustments (bonus/penalty system) tied to defect and downtime KPIs.
2. Downtime Cost Containment:
- Investigate September–November line operations — consider shift balancing or inventory preloading to reduce dependency during peaks.
3. Vendor Improvement Plans:
- Implement Supplier Quality Audits (SQAs) and Corrective Action Reports (CARs) for high-defect materials, especially Raw Materials and Corrugate.
