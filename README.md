# Customer Behavior Data Analysis Using SQL, Python, and Power BI

## 1. Introduction

Customer Behavior Data Analysis is an end-to-end data analytics project developed to demonstrate practical skills in Python, Pandas, SQL, PostgreSQL, and Power BI. The project focuses on analyzing customer purchasing patterns, spending behavior, product performance, subscription preferences, discount usage, shipping methods, customer loyalty, and revenue contribution across different age groups.

The project follows a structured data analytics workflow, beginning with raw customer shopping data, followed by data cleaning and transformation using Python, database management using PostgreSQL, business-oriented SQL analysis, and interactive visualization using Power BI.

The primary objective is to transform raw customer data into meaningful insights that can support business decision-making.

## 2. Project Objectives

The main objectives of this project are:

- To explore and understand customer shopping data using Python and Pandas.
- To identify and handle missing values and inconsistencies in the dataset.
- To perform feature engineering and prepare the data for further analysis.
- To store the cleaned dataset in a PostgreSQL database.
- To answer business-related questions using SQL queries.
- To develop an interactive Power BI dashboard for visualizing customer and sales trends.
- To identify patterns in customer spending, product preferences, subscription behavior, and discount usage.
- To derive actionable business insights that can support customer retention and marketing strategies.

## 3. Project Workflow

The project follows the workflow below:

Raw Customer Data  
↓  
Python and Pandas  
↓  
Data Cleaning and Transformation  
↓  
PostgreSQL Database  
↓  
SQL-Based Business Analysis  
↓  
Power BI Dashboard  
↓  
Business Insights and Recommendations

Each stage contributes to converting raw data into structured information that can be used for analytical and business purposes.

## 4. Dataset Description

The project uses a customer shopping dataset containing 3,900 purchase records and 18 original columns. The dataset includes information about customer demographics, purchased products, transaction amounts, subscription status, shipping preferences, discounts, and previous purchasing behavior.

### 4.1 Important Dataset Attributes

| Column | Description |
|---|---|
| Customer ID | Unique identifier assigned to each customer |
| Age | Age of the customer |
| Gender | Gender of the customer |
| Item Purchased | Product purchased by the customer |
| Category | Category to which the product belongs |
| Purchase Amount (USD) | Amount spent on the purchase |
| Location | Customer's location |
| Size | Size of the purchased product |
| Color | Color of the purchased product |
| Season | Season associated with the purchase |
| Review Rating | Rating provided by the customer |
| Subscription Status | Indicates whether the customer has a subscription |
| Shipping Type | Shipping method selected by the customer |
| Discount Applied | Indicates whether a discount was applied |
| Promo Code Used | Indicates whether a promotional code was used |
| Previous Purchases | Number of previous purchases made by the customer |
| Payment Method | Payment method used for the purchase |
| Frequency of Purchases | Reported frequency of customer purchases |

The initial dataset contains 37 missing values in the Review Rating column. These missing values are addressed during the data preparation stage.

## 5. Data Cleaning and Transformation Using Python

Python and Pandas are used to explore, clean, and transform the dataset before loading it into PostgreSQL.

### 5.1 Data Exploration

The following operations are performed to understand the dataset:

- Imported the CSV file into a Pandas DataFrame.
- Used `head()` to inspect the first few records.
- Used `info()` to examine column names, data types, and non-null values.
- Used `describe()` to calculate descriptive statistics.
- Used `isnull().sum()` to identify missing values in each column.

These steps provide an overview of the dataset's structure, quality, and statistical characteristics.

### 5.2 Handling Missing Values

The dataset contains 37 missing values in the Review Rating column. These values are imputed using the median review rating of the corresponding product category.

Using category-specific median values helps preserve differences in rating distributions between product categories while reducing the influence of extreme values.

### 5.3 Standardizing Column Names

Column names are standardized using the snake_case naming convention. This improves consistency and makes the columns easier to reference in Python and SQL.

For example, the column `purchase_amount_(usd)` is renamed to `purchase_amount`.

### 5.4 Feature Engineering

Two additional features are created to support customer segmentation and purchasing-frequency analysis.

**Age Group**

Customers are divided into four age groups:

- Young Adult
- Adult
- Middle-aged
- Senior

The groups are derived using age quartiles, allowing customers to be compared across different age segments. The exact age boundaries depend on the quartile values calculated from the dataset.

**Purchase Frequency in Days**

The categorical purchase-frequency values are mapped to approximate numerical intervals.

| Purchase Frequency | Approximate Interval (Days) |
|---|---:|
| Weekly | 7 |
| Fortnightly | 14 |
| Bi-Weekly | 14 |
| Monthly | 30 |
| Quarterly | 90 |
| Every 3 Months | 90 |
| Annually | 365 |

This transformation makes the frequency information easier to use in numerical analysis. The mapped values are approximations rather than measured intervals between actual transactions.

### 5.5 Removing Redundant Columns

The `discount_applied` and `promo_code_used` columns are compared to determine whether they contain identical information. After confirming that both columns contain the same values in this dataset, `promo_code_used` is removed to avoid redundant information.

## 6. Database Management and SQL Analysis

After cleaning and transformation, the prepared dataset is loaded into PostgreSQL using Python and SQLAlchemy.

### 6.1 Database Configuration

- **Database Name:** `customer_behavior`
- **Table Name:** `customer`
- **Database System:** PostgreSQL

PostgreSQL is used to store the cleaned dataset and perform structured queries for business analysis.

### 6.2 Business Questions Addressed Using SQL

SQL queries are developed to investigate the following questions:

1. What is the total revenue generated by male and female customers?
2. Which customers used discounts but spent more than the average purchase amount?
3. Which five products have the highest average review ratings?
4. How do average purchase amounts differ between Standard and Express Shipping?
5. Do subscribed customers have a higher average purchase amount than non-subscribed customers?
6. Which five products have the highest percentage of purchases with discounts applied?
7. How can customers be segmented into New, Returning, and Loyal groups based on their previous purchases?
8. What are the three most frequently purchased products within each category?
9. Are customers with more than five previous purchases more likely to subscribe?
10. What is the revenue contribution of each age group?

These questions focus on customer behavior, product performance, revenue distribution, and potential opportunities for improving customer retention and marketing effectiveness.

### 6.3 SQL Concepts Applied

The analysis demonstrates the use of the following SQL concepts:

- `SELECT` and `WHERE` clauses
- `GROUP BY` and `ORDER BY`
- Aggregate functions, including `SUM()`, `AVG()`, and `COUNT()`
- Subqueries
- Conditional logic using `CASE`
- Common Table Expressions (CTEs)
- Window functions, including `ROW_NUMBER()`

These techniques support data aggregation, filtering, segmentation, ranking, and comparative analysis.

## 7. Power BI Dashboard Development

An interactive Customer Behavior Dashboard is developed using Power BI to present the analyzed data in a clear and accessible format.

The dashboard enables users to explore customer demographics, revenue distribution, product categories, and subscription patterns through visual representations and interactive filters.

### 7.1 Key Performance Indicators

The dashboard includes the following KPI cards:

- Number of Customers
- Average Purchase Amount
- Average Review Rating

These indicators provide a high-level overview of the dataset and its purchasing characteristics.

### 7.2 Data Visualizations

The dashboard contains the following visualizations:

- Percentage of Customers by Subscription Status
- Revenue by Product Category
- Sales by Product Category
- Revenue by Age Group
- Sales by Age Group

These visualizations help identify differences in purchasing behavior across customer segments and product categories.

### 7.3 Interactive Filters

The dashboard includes slicers for:

- Subscription Status
- Gender
- Product Category
- Shipping Type

Users can apply these filters to examine specific customer segments and compare how the selected attributes relate to sales, revenue, and purchasing behavior.

### 7.4 Dashboard Applications

The dashboard is designed to help business stakeholders investigate questions such as:

- Which customer groups contribute the most revenue?
- Which product categories record higher sales?
- How does revenue vary across age groups?
- How do purchasing metrics differ between subscribed and non-subscribed customers?
- How do average purchase amounts vary by shipping type?
- How do customer and sales patterns change when filtering by gender or category?

The dashboard provides a consolidated view of customer shopping data and supports exploratory analysis through interactive visualizations.

## 8. Business Analysis Areas

### 8.1 Customer Segmentation

Customers are categorized into New, Returning, and Loyal groups using their previous purchase counts.

This segmentation helps distinguish customers with limited purchasing history from those who demonstrate repeat purchasing behavior. Businesses can use these groups to develop targeted retention campaigns, loyalty programs, and customer engagement strategies.

### 8.2 Subscription Analysis

Subscription behavior is evaluated by comparing customer counts, average purchase amounts, total revenue, and repeat purchasing indicators.

The analysis helps identify differences between subscribed and non-subscribed customers. However, differences in spending alone do not establish that subscriptions cause higher spending.

### 8.3 Product Performance Analysis

Product-level analysis is used to identify frequently purchased products, highly rated products, and products associated with discount usage.

Ranking products within their respective categories helps reveal product preferences and provides a basis for reviewing product performance and promotional strategies.

### 8.4 Discount Analysis

Discount usage is examined in relation to purchase amounts and product-level discount rates.

The analysis identifies purchases in which customers received discounts but still spent more than the dataset's average purchase amount. It also highlights products with relatively high discount usage.

These findings can support further investigation into promotional effectiveness. However, profitability cannot be determined without additional information about product costs and margins.

### 8.5 Age Group Analysis

Revenue and sales are compared across Young Adult, Adult, Middle-aged, and Senior customer groups.

This analysis provides an overview of purchasing differences across age segments and can help businesses evaluate whether their marketing strategies align with the characteristics of different customer groups.

## 9. Technologies Used

| Technology | Purpose |
|---|---|
| Python | Data exploration, analysis, and preparation |
| Pandas | Data cleaning, transformation, and feature engineering |
| PostgreSQL | Database storage and structured data analysis |
| SQL | Business-question analysis and customer segmentation |
| Power BI | Interactive dashboards and data visualization |
| Jupyter Notebook | Development and execution of Python analysis |
| SQLAlchemy | Connecting Python to PostgreSQL and loading data |
| psycopg2 | PostgreSQL database connectivity for Python |

## 10. Project Directory Structure

The project repository is organized as follows:

```text
customer-behavior-data-analysis/
│
├── customer_shopping_behavior.csv
├── Customer_Shopping_Behavior_Analysis.ipynb
├── customer_behavior_sql_queries.sql
├── customer_behavior_dashboard.pbix
├── README.md
│
└── screenshots/
    └── customer_behavior_dashboard.png
```

The filenames can be modified to match the actual files available in the GitHub repository.

## 11. Implementation Procedure

### Step 1: Clone the Repository

Clone the project repository and navigate to the project directory.

```bash
git clone <your-github-repository-url>
cd <your-project-folder>
```

### Step 2: Set Up the Python Environment

Open the Jupyter Notebook named `Customer_Shopping_Behavior_Analysis.ipynb`.

Install the required Python packages if they are not already available.

```bash
pip install pandas sqlalchemy psycopg2-binary jupyter
```

### Step 3: Execute Data Preparation

Run the notebook cells to perform the following operations:

- Import the CSV dataset.
- Explore the dataset and calculate descriptive statistics.
- Identify and handle missing values.
- Standardize column names.
- Create the `age_group` feature.
- Create the `purchase_frequency_days` feature.
- Compare and remove redundant columns.

### Step 4: Configure PostgreSQL

Create a PostgreSQL database named `customer_behavior`.

Configure the database connection in the Python notebook and load the cleaned DataFrame into a table named `customer` using SQLAlchemy.

Database credentials should be configured securely rather than stored directly in publicly shared notebook code.

### Step 5: Execute SQL Queries

Open `customer_behavior_sql_queries.sql` and execute the queries against the PostgreSQL `customer` table.

Review the results to understand customer spending, product ratings, subscription behavior, discount usage, and revenue distribution.

### Step 6: Open the Power BI Dashboard

Open `customer_behavior_dashboard.pbix` in Power BI Desktop.

Configure the PostgreSQL connection and use the prepared customer table as the data source. Refresh the data if required, then interact with the dashboard using the available slicers and visualizations.

## 12. Key Dataset Statistics

The initial dataset contains the following characteristics:

| Attribute | Value |
|---|---:|
| Total purchase records | 3,900 |
| Original columns | 18 |
| Distinct products | 25 |
| Product categories | 4 |
| Customer locations | 50 |
| Shipping types | 6 |
| Payment methods | 6 |
| Purchase-frequency categories | 7 |
| Gender categories | 2 |
| Subscription statuses | 2 |
| Missing review ratings | 37 |

Additional descriptive statistics calculated during the initial data exploration include:

- Average purchase amount: approximately USD 59.76
- Average review rating: approximately 3.75
- Average customer age: approximately 44 years
- Average number of previous purchases: approximately 25

These figures describe the initial dataset and should be verified against the actual dataset and notebook outputs before being reported as final results.

## 13. Business Value

This project demonstrates how data analytics techniques can be applied to a retail customer dataset to generate useful business information.

The integrated workflow connects data cleaning, database management, SQL analysis, and dashboard development within a single project.

The analysis can help businesses:

- Understand customer purchasing patterns.
- Compare spending behavior across customer segments.
- Identify frequently purchased and highly rated products.
- Examine subscription and discount usage.
- Evaluate revenue contribution across product categories and age groups.
- Develop more informed customer retention and marketing strategies.

The findings provide a foundation for further analysis, although additional transaction history, product cost data, and time-based information would be required to evaluate customer lifetime value, profitability, and long-term purchasing trends reliably.

## 14. Skills Demonstrated

### Data Analysis
- Exploratory data analysis
- Descriptive statistics
- Missing-value handling
- Data quality assessment
- Feature engineering
- Customer segmentation
- Business-question formulation

### Python and Pandas
- DataFrame operations
- Data cleaning and transformation
- Group-based median imputation
- Categorical-to-numerical mapping
- Column standardization
- Data validation

### SQL and PostgreSQL
- Data filtering and aggregation
- Grouping and sorting
- Subqueries and CTEs
- Conditional statements using `CASE`
- Window functions and ranking
- Customer and product-level analysis
- Loading and querying structured data

### Power BI
- KPI cards
- Bar charts and category comparisons
- Donut charts
- Interactive slicers
- Cross-filtering
- Dashboard design
- Data storytelling

### Database Integration
- PostgreSQL database management
- SQLAlchemy connectivity
- Loading Pandas DataFrames into PostgreSQL
- Connecting Power BI to a database

## 15. Future Improvements

The project can be extended in several ways to provide deeper analytical insights.

- **Sales Trend Analysis:** Introduce transaction dates to examine monthly, quarterly, and seasonal purchasing patterns.
- **RFM Segmentation:** Use Recency, Frequency, and Monetary metrics when suitable transaction-level history is available.
- **Geographical Analysis:** Develop map-based visualizations to compare customer distribution and purchasing behavior across locations.
- **Customer Lifetime Value:** Estimate customer lifetime value when sufficient historical purchasing and profitability data are available.
- **Profitability Analysis:** Incorporate product costs and profit margins to evaluate whether discount strategies improve profitability.
- **Advanced Power BI Measures:** Implement additional DAX measures for growth rates, comparative KPIs, and customer retention metrics.
- **Executive Summary:** Add a dedicated dashboard page highlighting the most important findings and recommendations.
- **Automated Data Refresh:** Configure an appropriate refresh workflow to keep the dashboard updated when the underlying database changes.

## 16. Conclusion

The Customer Behavior Data Analysis project demonstrates an end-to-end approach to analyzing retail shopping data using Python, Pandas, PostgreSQL, SQL, and Power BI.

The project begins with data exploration and cleaning, followed by feature engineering, database integration, SQL-based business analysis, and interactive dashboard development. This structured workflow demonstrates how raw customer data can be transformed into meaningful information for understanding purchasing patterns, product performance, subscription behavior, discount usage, and revenue distribution.

The project also provides practical experience in data preparation, relational database querying, analytical problem-solving, and business intelligence visualization. These skills are relevant to entry-level Data Analyst and Business Analyst roles and provide a foundation for more advanced retail analytics projects.

## 17. License

This project is intended for educational purposes, learning, and portfolio development. Any redistribution or reuse of the dataset and related materials should comply with their applicable licensing and usage terms.

## About the Project

This project presents an integrated customer analytics workflow using Python, SQL/PostgreSQL, and Power BI. Its purpose is to demonstrate the application of data analysis and business intelligence techniques to customer shopping data and convert the resulting analysis into useful business insights.
