# Porter Delivery & Order Analytics

## Project Overview

This project analyzes Porter food-delivery order data to identify
operational patterns, delivery-performance drivers, market differences,
and order-value trends.

The analysis was completed in Microsoft Excel using data cleaning,
transformation, statistical analysis, correlation, regression, outlier
detection, Pivot Tables, and dashboarding.

## Business Objectives

The project investigates:

-   Order volume across markets
-   Delivery efficiency by order protocol
-   Average order value by market
-   Peak-hour delivery performance
-   Relationship between order size and delivery time
-   Weekly delivery-time patterns
-   Relationship between item price range and subtotal
-   Restaurant-category contribution to above-average orders
-   Delivery-time variability and outliers
-   Delivery-partner utilization and delivery performance

## Dataset

The workbook contains approximately 197,421 order records.

### Main fields

  Field                        Description
  ---------------------------- -----------------------------
  `market_id`                  Market identifier
  `created_at`                 Order creation timestamp
  `actual_delivery_time`       Actual delivery timestamp
  `store_id`                   Restaurant/store identifier
  `store_primary_category`     Primary restaurant category
  `order_protocol`             Order protocol
  `total_items`                Total items in the order
  `subtotal`                   Order subtotal
  `num_distinct_items`         Number of distinct items
  `min_item_price`             Minimum item price
  `max_item_price`             Maximum item price
  `total_onshift_partners`     Delivery partners on shift
  `total_busy_partners`        Busy delivery partners
  `total_outstanding_orders`   Outstanding orders

### Derived fields

The cleaned dataset includes additional fields such as:

-   `Market_IdLabel`
-   `Store_idclean`
-   `Order_protocolLabel`
-   `delivery_duration_min`
-   `Order_hour`
-   `Order_dayofweek`
-   `price_range`
-   `is_above_avg_subtotal`
-   `delivery_outlier`
-   `Busy_to_onshift_ratio`
-   `Outstanding_toshift_ratio`

## Tools & Techniques

### Tools

-   Microsoft Excel
-   Excel Tables
-   Pivot Tables
-   Pivot Charts
-   Excel formulas
-   Power Query / data transformation concepts

### Analytical techniques

-   Data cleaning
-   Missing-value handling
-   Feature engineering
-   Grouped aggregation
-   Correlation analysis
-   Regression analysis
-   Standard deviation
-   IQR-based outlier detection
-   Business interpretation
-   Dashboard development

# Key Findings

## 1. Order Protocol Efficiency

-   Protocol 7 has the lowest average delivery time at approximately
    **41.36 minutes**, although it has relatively low order volume.
-   Protocol 6 has the highest average delivery time at approximately
    **61.09 minutes**.
-   Among protocols with meaningful order volume, Protocol 5 performs
    particularly well.

**Insight:** The fastest protocol should not be evaluated only by
average speed; order volume and operational relevance should also be
considered.

## 2. Average Order Value by Market

-   Market 4 has the highest average order value at approximately
    **28.96**.
-   Market 5 has the lowest at approximately **24.12**.

**Insight:** Market 4 combines strong order volume with high average
order value, while lower-value markets may benefit from
basket-size-building strategies.

## 3. On-Shift Partners vs Delivery Time During Peak Hours

For peak hours defined in the analysis as Order_hour 1, 2, and 3:

-   Peak-hour orders: approximately **92,228**
-   Correlation between on-shift partners and delivery duration:
    approximately **-0.036**

**Insight:** There is effectively no meaningful linear relationship
between on-shift partner count and delivery duration during these peak
hours. Other factors such as restaurant preparation time, routing,
distance, and congestion may be more important.

## 4. Order Size vs Delivery Time

  Relationship                            Correlation
  ------------------------------------- -------------
  Total Items vs Delivery Duration            \~0.005
  Distinct Items vs Delivery Duration         \~0.007

The regression model also has an extremely low R-squared.

**Insight:** Order size has a negligible relationship with delivery
duration in this dataset. Delivery performance is likely influenced more
by operational factors such as distance, restaurant load, traffic, and
partner allocation.

## 5. Delivery Time Across the Week

-   Weekday average delivery time: approximately **46.87 minutes**
-   Weekend average delivery time: approximately **51.40 minutes**
-   Range across the week: approximately **8.25 minutes**

**Insight:** Weekends are somewhat slower, but the data does not show a
simple weekday-versus-weekend pattern. Individual days appear to
contribute differently to operational pressure.

## 6. Price Range vs Subtotal

Correlation between `price_range` and `subtotal`:

**\~0.51**

**Insight:** There is a moderate positive relationship. Orders
containing a wider range of item prices tend to have higher subtotals.

## 7. Restaurant Category and Above-Average Orders

Overall average subtotal:

**\~26.82**

-   Burmese orders are above average approximately **67.6%** of the
    time.
-   Convenience-Store orders are above average approximately **9.2%** of
    the time.

**Insight:** Restaurant category is associated with meaningful
differences in order value. High-value categories can be considered for
premium promotions and upselling, while low-value categories may benefit
from combo offers and minimum-order incentives.

## 8. Delivery-Time Variability

### Market-level results

  Market       Orders   Avg Delivery (min)   Std. Dev. (min)
  ---------- -------- -------------------- -----------------
  Market 1     38,037                55.21            728.45
  Market 2     56,042                46.11             17.97
  Market 3     23,296                47.70             19.93
  Market 4     47,597                47.37             33.67
  Market 5     17,999                46.50             17.88
  Market 6     14,450                47.26             19.80

Market 1 has both the highest average delivery time and extremely high
variability.

### Categories with high variance

  Category         Orders   Avg Delivery (min)   Std. Dev. (min)
  -------------- -------- -------------------- -----------------
  Italian           7,179                70.20          1,674.84
  Dessert           8,772                48.79             69.10
  Indian            7,314                49.74             67.46
  Afghan              119                51.67             27.89
  Comfort-Food         28                51.03             26.16

**Insight:** Market 1 is a major operational concern because delivery is
both slower and less predictable. Italian and Dessert categories also
show substantial variation.

## 9. Busy-to-On-Shift Partner Ratio

  Market       Avg Delivery (min)   Avg Busy/On-Shift Ratio   Correlation
  ---------- -------------------- ------------------------- -------------
  Market 1                  55.21                      0.96       \~0.003
  Market 2                  46.11                      0.97       \~0.017
  Market 3                  47.70                      0.90       \~0.166
  Market 4                  47.37                      0.97       \~0.025
  Market 5                  46.50                      0.86       \~0.080
  Market 6                  47.26                      0.93       \~0.023

**Insight:** Most markets show only a weak relationship between partner
saturation and delivery time. Simply increasing partner availability may
not fully solve delivery delays.

# Workbook Structure

  Sheet          Purpose
  -------------- ---------------------------------------------
  `dataset`      Original order-level dataset
  `Clean`        Cleaned and transformed dataset
  `Dashboard`    Dashboard and visual summary
  `Easy`         Introductory business analysis
  `Medium`       Detailed analytical questions and findings
  `Summary`      Consolidated summary tables
  `STDEV`        Standard-deviation and variability analysis
  `Imputation`   Missing-value analysis/imputation
  `Sheet5`       Supporting calculations

# Data Preparation

The project includes:

1.  Reviewing the original dataset
2.  Cleaning categorical values
3.  Creating readable market, store, and protocol labels
4.  Calculating delivery duration
5.  Extracting order hour and day of week
6.  Creating price-range features
7.  Creating above-average-subtotal indicators
8.  Identifying delivery-time outliers using the IQR method
9.  Creating partner-utilization ratios
10. Building market, category, store, and protocol summaries

# Business Recommendations

### 1. Investigate Market 1

Market 1 requires detailed investigation because of its high average
delivery time and exceptionally high variability.

### 2. Prioritize protocols with meaningful volume

Consider both delivery speed and order volume when evaluating protocol
performance.

### 3. Look beyond partner headcount

The weak correlations suggest that delivery delays cannot be explained
by partner availability alone.

### 4. Target high-value categories

Categories with a high percentage of above-average orders can be
targeted with premium promotions and upselling.

### 5. Increase basket size

Lower-value markets and categories can be targeted with combo offers,
cross-selling, and minimum-order incentives.

### 6. Focus on consistency

Reducing delivery-time variability can be as important as reducing
average delivery time because customers value predictable delivery.

# Important Analytical Note

Correlation measures association, not causation. A weak correlation does
not prove that a factor has no operational effect, and a positive
correlation does not prove that one variable causes the other.

# How to Use

1.  Open `FinalPorter_Project_Manisha.xlsx`.
2.  Start with the `Dashboard` sheet for the high-level view.
3.  Review `Clean` to understand the transformed data.
4.  Review `Easy` for introductory analysis.
5.  Review `Medium` for detailed business questions and statistical
    analysis.
6.  Review `Summary` and `STDEV` for supporting calculations.

# Project Outcome

This project demonstrates practical Excel-based data analytics and
business intelligence skills, including data cleaning, feature
engineering, statistical analysis, correlation, regression, outlier
analysis, visualization, and business storytelling.

## Author

**Manisha Mali**

### Skills Demonstrated

-   Microsoft Excel
-   Data Analytics
-   Data Cleaning
-   Statistical Analysis
-   Correlation Analysis
-   Regression Analysis
-   Outlier Analysis
-   Data Visualization
-   Business Analysis
-   Business Intelligence
