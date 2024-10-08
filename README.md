# Credit Card Financial Dashboard
![Banner]([path/to/your/image.png](https://i.ytimg.com/vi/8tfcVnoEL0c/maxresdefault.jpg)

## Table of Contents

1. [Project Objective](#project-objective)
2. [Data from SQL](#data-from-sql)
3. [Data Processing & DAX](#data-processing--dax)
4. [Dashboard & Insights](#dashboard--insights)
5. [Export & Share Project](#export--share-project)
6. [Project Insights](#project-insights)
7. [Add to Resume](#add-to-resume)

## Project Objective

The objective of this project is to develop a comprehensive **Credit Card Weekly Dashboard** that provides real-time insights into key performance metrics and trends, enabling stakeholders to effectively monitor and analyze credit card operations. The dashboard will help decision-makers identify revenue opportunities, track customer behavior, and manage overall performance.

## Data from SQL

The project utilizes data stored in a PostgreSQL database. Key steps involved:

1. **Prepare CSV Files**: Import data related to credit card transactions and customer details.
2. **Create Tables in SQL**: Use SQL queries to create relevant tables such as `cc_detail` and `cust_detail`.
3. **Import CSV Files into SQL**: Load the prepared CSV files into the created SQL tables.

## Data Processing & DAX

In Power BI, **DAX (Data Analysis Expressions)** queries were used to process and calculate important metrics such as customer age groups, income categories, weekly revenue, and comparisons. Some key DAX queries include:

```dax
-- Age Group Classification
AgeGroup = SWITCH(
    TRUE(),
    'public cust_detail'[customer_age] < 30, "20-30",
    'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
    'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
    'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
    'public cust_detail'[customer_age] >= 60, "60+",
    "unknown"
)

```
```
-- Income Group Classification
IncomeGroup = SWITCH(
    TRUE(),
    'public cust_detail'[income] < 35000, "Low",
    'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
    'public cust_detail'[income] >= 70000, "High",
    "unknown"
)
```
```
-- Weekly Revenue Calculation
week_num2 = WEEKNUM('public cc_detail'[week_start_date])
Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]

Current_week_Reveneue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
    FILTER(
        ALL('public cc_detail'),
        'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])
    )
)
```
```
Previous_week_Reveneue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
    FILTER(
        ALL('public cc_detail'),
        'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2]) - 1
    )
)
```
## Dashboard & Insights

### Weekly Insights (Week 53 - 31st Dec):
- **Revenue**: Increased by 28.8%
- **Total Transaction Amount & Count**: Increased by `xx%` & `xx%`
- **Customer Count**: Increased by `xx%`

### Year-To-Date Overview:
- **Total Revenue**: $57M
- **Total Interest**: $8M
- **Total Transaction Amount**: $46M

### Gender Insights:
- **Male Customers**: $31M
- **Female Customers**: $26M

### Card Performance:
- **Blue & Silver cards**: Contribute to 93% of overall transactions.

### Top States:
- **Texas, New York, and California**: Contribute 68% of total transactions.

### Additional Metrics:
- **Overall Activation Rate**: 57.5 %
- **Overall Delinquent Rate**: 6.06 %

## Export & Share Project

To share the project with stakeholders:

1. Export the dashboard from Power BI as a `.pbix` file.
2. Share the `.pbix` file or publish it on the Power BI service for access.
3. Schedule regular updates for the dashboard to ensure real-time insights.

## Project Insights

This project provides stakeholders with a comprehensive view of credit card operations, allowing for the effective monitoring of key metrics such as revenue growth, customer segmentation, and transaction performance.

## Add to Resume

**Credit Card Financial Dashboard using Power BI**:
- Developed an interactive dashboard using transaction and customer data from a SQL database to provide real-time insights.
- Streamlined data processing & analysis to monitor key performance metrics and trends.
- Shared actionable insights with stakeholders based on dashboard findings to support decision-making processes.



