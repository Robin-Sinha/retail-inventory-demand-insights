# Retail Inventory & Demand Insights

## Project Overview

This project uses Power BI to look at retail inventory and demand
patterns in a simulated dataset. The aim is to spot areas where stock
may need a closer look and understand how demand changes across
categories, promotions, discounts and months.

## Business Problem

How can a retailer use inventory and demand data to spot possible
overstocking or stockout risk and make better stock planning decisions?

## Business Questions

1.  How many records are flagged as potential overstock or stockout
    risk?
2.  How do average inventory and demand compare across categories?
3.  Which regions and store-category combinations show higher
    stockout-risk rates?
4.  How do demand, units sold and units ordered compare across
    categories?
5.  Do records with promotions show different demand and sales patterns?
6.  How does average demand vary at different discount levels?
7.  How does demand change from month to month?

## Dataset

-   **Source:** [Kaggle -- Demand Forecasting
    Dataset](https://www.kaggle.com/datasets/raminhuseyn/demand-forecasting-dataset)
-   **Size:** About 76,000 rows and 16 columns.
-   **Period:** January 2022 to January 2024.
-   **Type:** Simulated retail data. It is not real retailer or customer
    data.

The source columns include `Date`, `Store ID`, `Product ID`, `Category`,
`Region`, `Inventory Level`, `Units Sold`, `Units Ordered`, `Price`,
`Discount`, `Weather Condition`, `Promotion`, `Competitor Pricing`,
`Seasonality`, `Epidemic` and `Demand`.

## Data Checks and Preparation

-   Checked the data and reviewed its quality.
-   The dataset was mostly clean so only basic checks were needed.
-   Created a separate Calendar table based on the date range in the
    dataset.
-   Added `Year`, `Quarter`, `Month`, `Month Number`, `Month Start` and
    `Year-Month` fields.
-   Marked the Calendar table as a date table and linked it to the main
    table using the date field.
-   Sorted the month fields so charts display dates in the correct
    order.

## Calculated Columns

### Inventory Risk

Created an `Inventory Risk` column to group records into three
categories: - **Stockout Risk:** Inventory Level is lower than Demand. -
**Potential Overstock:** Inventory Level is more than 1.5 times
Demand. - **Balanced:** The record does not meet either rule.

The 1.5-times threshold is a working rule for this project. It is not an
industry standard. These labels highlight records for review but do not
confirm actual stockouts or excess stock.

### Promotion Status

Created a `Promotion Status` column to make the numeric values easier to
read: - `0` = No Promotion - `1` = Promotion

## DAX Measures

These measures were created for the dashboard:

  -----------------------------------------------------------------------
  Measure                             What it shows
  ----------------------------------- -----------------------------------
  `Total Records`                     Total number of rows.

  `Avg Demand`                        Average recorded demand.

  `Avg Inventory`                     Average inventory level.

  `Avg Inventory Gap`                 Average inventory minus average
                                      demand.

  `Potential Overstock Records`       Number of records labelled
                                      Potential Overstock.

  `Potential Overstock %`             Percentage of records labelled
                                      Potential Overstock.

  `Stockout Risk Records`             Number of records labelled Stockout
                                      Risk.

  `Stockout Risk %`                   Percentage of records labelled
                                      Stockout Risk.
  -----------------------------------------------------------------------

The measures update when Store ID, Date or Category slicers are used.

## Dashboard Pages

### Page 1 --- Inventory Overview & Risk

This page gives an overview of inventory and potential risk. It
includes: - Total records, potential overstock percentage, average
inventory gap and stockout-risk percentage. - Inventory-risk
distribution. - Stockout risk by region. - Average inventory compared
with demand by category. - Inventory and demand trends over time. - A
matrix showing stockout-risk percentages by store and category. - Key
findings from the analysis.

### Page 2 --- Demand Patterns

This page looks at how demand varies across categories and other
factors. It includes: - Average demand and units sold by promotion
status. - Monthly average demand trend. - Average demand, units sold and
units ordered by category. - Average demand and units sold by discount
level. - Key findings and business recommendations.

Both pages have synced Store ID, Date and Category slicers.

## Key Findings

-   71.5% of records were flagged as potential overstock and 13.7% were
    flagged as stockout risk using the rules set for this project.
-   Groceries had the largest average gap between inventory and demand
    at about 239 units.
-   Records with promotions had higher average demand and units sold
    than records without promotions.
-   Average demand was highest at discount level 20 and dipped slightly
    at level 25.
-   Monthly demand went up and down during the period instead of
    following a steady trend.

These are patterns in simulated data. They do not prove that promotions,
discounts or other factors caused demand to change.

## Business Recommendations

-   Review categories where average inventory is much higher than
    demand.
-   Take a closer look at store-category combinations with higher
    stockout-risk rates.
-   Compare promotion and discount patterns with demand and sales before
    changing the strategy.
-   Use monthly demand trends to help plan replenishment. Check whether
    patterns repeat before making seasonal decisions.

## Tools Used

-   Power BI Desktop
-   Power Query for data checks
-   DAX measures and calculated columns
-   Calendar table and date relationships
-   Charts, KPI cards, slicers and conditional formatting

## Conclusion

This project shows how Power BI can help explore inventory data and
highlight areas that may need further review. The dashboard brings
inventory risks and demand patterns together to support better questions
about stock planning.

## Disclaimer

The dataset is simulated and does not represent a real retailer or
actual customer transactions. Inventory-risk labels use working rules
created for this project. The results are indicators for further
analysis rather than confirmed business outcomes.
