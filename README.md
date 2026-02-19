# Project Overview

Grifols S.A. is a leading global healthcare company, founded in Spain in 1909, specializing in plasma-derived medicines. With a global presence across 110 countries and over 23,800 employees, Grifols is a major player in blood plasma-based products, biopharmaceuticals, transfusion medicine, and clinical diagnostic technologies.

## Analysis

This analysis aims to understand donor behavior and associated costs, focusing on trending patterns of donations and costs over time, and evaluating the effectiveness of different compensation structures at various donation centers. The primary objectives are to answer the following business questions:

1.  **How are costs and donations trending over time?** Is there a particular center contributing in an outsized way to the overall performance trend?
2.  **Which compensation structure is most effective** at driving total donations? Which compensation structure is most cost-effective?
3.  **Balancing the two above, what is your strategic recommendation for compensation** going forward?

## Datasets

To achieve these objectives, two datasets are utilized:

*   **Return Donor Donations:** Contains information on donation centers, donor IDs, and donation dates.
*   **Return Donor Fees:** Provides details on the fees offered to donors by each data center.

## Summary:

### How are costs and donations trending over time? Is there a particular center contributing in an outsized way to the overall performance trend?

Costs and donations exhibit strong weekly seasonality across all centers. Center A is the top performer, attracting significantly more unique donors and total donations compared to Centers B and C, thus contributing in an outsized way to the overall donation volume. However, Center A also incurs the highest associated costs. Centers B and C show comparable performance to each other, but are notably lower than Center A in terms of donations and unique donors, with similar cost structures.

### Which compensation structure is most effective at driving total donations? Which compensation structure is most cost-effective?

Center A's compensation structure (1st donation: \$40, 2nd donation: \$70) appears most effective at driving total donations, as it yields the highest donation volumes. However, Donation Center C is the most cost-effective in terms of Cost Per Donation and in driving higher returning rates.
To determine cost-effectiveness, further analysis of the cost per donation is required. While Center A has the highest total costs, its higher volume might result in a competitive cost per donation due to economies of scale.

### Balancing the two above, what is your strategic recommendation for compensation going forward?

The strategic recommendation is to leverage Center A's success by analyzing and piloting its compensation structure in Centers B and C. This should be combined with optimizing second donation incentives, implementing a tiered compensation model for donor loyalty, and exploring dynamic pricing strategies. Continuous A/B testing of compensation models is crucial to balance increased donations with cost efficiency.

## Data Analysis Key Findings

### Data Preparation

* `donation_date` was converted to datetime, and features like `day`, `month`, `year`, `weekday`, and `week` were extracted.
* A `first_or_second` indicator was developed to differentiate donations within a week, and `amount` was calculated based on center-specific fee structures (e.g., Center A: \$40 for 1st, \$70 for 2nd).

### Statistical Differences Among Centers

* Levene's test confirmed equal variances of donations per week across centers (p-value = 0.961904), allowing for valid comparisons.
* Tukey's test revealed significant differences: Center A significantly outperformed Center B (averaging 261 more donations per week) and Center C (averaging 238 more donations per week).
* No significant statistical difference was found between Center B and Center C (p-tukey = 0.889805).

### Center Performance
* **Center A**: 28,707 donations from 2,022 unique donors, with \$1.49 million in costs.
* **Center B**: 21,659 donations from 1,859 unique donors, with \$1.16 million in costs.
* **Center C**: 22,263 donations from 1,523 unique donors, with \$1.14 million in costs.

### Donor Behavior Insights

* Donors show a preference for mid-month and Thursday donations.
* Approximately 40% of donors make a second donation within the same week, highlighting the importance of second donation incentives.


## Time Series Analysis

*   All donation and cost time series exhibited clear weekly seasonality (period=7) and were found to be non-stationary (ADF test p-values > 0.05).
*   AutoARIMA models were used for 60-day forecasts, with residuals showing no significant correlation (Ljung-Box Q Test p-values > 0.05), indicating a good fit.
*   **Forecast Accuracy (MAPE)**:
  * Donations: Center A (6.26%), Center B (12.02%), Center C (13.95%).
  * Costs: Center A (6.10%), Center B (11.85%), Center C (15.58%).

### Insights or Next Steps

*   **Strategic Compensation Review**: Evaluate the cost-per-donation for each center. Consider piloting Center A's compensation structure or elements thereof in Centers B and C to assess its impact on donation volumes and overall cost-effectiveness, while also optimizing second donation incentives.
*   **Advanced Analytics**: Implement detailed donor segmentation, explore the impact of external factors on donation behavior, and conduct causal inference studies to understand the direct effect of compensation changes versus other confounding variables.

