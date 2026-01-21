# Customer Shopping Behavior Analysis

## Project Overview

This project analyzes customer shopping behavior using transactional data from 3,900 purchases across various product categories. The analysis leverages **Python** for data cleaning and preparation, **PostgreSQL** for structured business analytics, and **Power BI** for interactive visualization. The goal is to uncover actionable insights into spending patterns, customer segmentation, product preferences, and subscription behavior to guide strategic business decisions.

## Dataset Description

**Size:** 3,900 rows × 18 columns

**Key Features:**
- **Customer Demographics:** Age, Gender, Location, Subscription Status
- **Purchase Details:** Item Purchased, Category, Purchase Amount (USD), Season, Size, Color
- **Shopping Behavior:** Discount Applied, Promo Code Used, Previous Purchases, Frequency of Purchases, Review Rating, Shipping Type, Payment Method

**Data Quality:** 37 missing values identified in the Review Rating column

## Technologies Used

- **Python:** pandas, psycopg2, SQLAlchemy
- **Database:** PostgreSQL
- **Visualization:** Power BI
- **Development Environment:** Jupyter Notebook/Google Colab

## Project Workflow

### 1. Data Preparation & Cleaning (Python)

**Data Loading & Exploration**
- Imported dataset using pandas and performed initial exploration with `.info()` and `.describe()`
- Assessed data structure, types, and statistical distributions

**Missing Data Handling**
- Identified 37 null values in Review Rating column
- Applied category-wise median imputation to preserve rating patterns within product categories

**Column Standardization**
- Converted all column names to snake_case for consistency
- Renamed `Purchase Amount (USD)` to `purchase_amount` for cleaner querying

**Feature Engineering**
- Created `age_group` column by segmenting customers into quartiles: Young Adult, Adult, Middle-aged, and Senior
- Developed `purchase_frequency_days` column by mapping textual frequency descriptions (Weekly, Monthly, etc.) to numerical day intervals

**Data Consistency Check**
- Verified that `discount_applied` and `promo_code_used` columns were redundant (100% correlation)
- Dropped `promo_code_used` to eliminate duplicate information

**Database Integration**
- Established connection to PostgreSQL using SQLAlchemy
- Loaded cleaned DataFrame into database table for SQL-based analysis

### 2. Business Analytics (SQL)

Performed structured analysis in PostgreSQL to extract key business insights:

**Revenue Analysis by Demographics**
- Analyzed total revenue contribution by gender to understand purchasing power distribution
- Calculated revenue by age group to identify high-value customer segments

**Discount & Pricing Strategy**
- Identified customers who used discounts but maintained high purchase amounts, revealing price-sensitive yet valuable customers
- Determined which products had the highest discount utilization rates to evaluate promotional effectiveness

**Product Performance Metrics**
- Ranked products by average review ratings to identify top-performing items
- Listed the top 3 most purchased products within each category to understand category-specific preferences

**Shipping Behavior Analysis**
- Compared average purchase amounts between Standard and Express shipping to correlate urgency with spending

**Subscription Impact Assessment**
- Evaluated spending differences between subscribers and non-subscribers in terms of average spend and total revenue
- Analyzed repeat buyer behavior (customers with >5 previous purchases) to assess subscription likelihood

**Customer Segmentation**
- Classified customers into three segments based on purchase history:
  - **New:** 1 previous purchase
  - **Returning:** 2-10 previous purchases
  - **Loyal:** 11+ previous purchases
- This segmentation enables targeted marketing strategies for each customer lifecycle stage

### 3. Data Visualization (Power BI)

Built an interactive dashboard to visualize key findings and enable dynamic exploration of customer behavior patterns, revenue trends, and product performance metrics.

## Key Business Insights

**Customer Loyalty & Retention**
- Segmentation analysis reveals the distribution of customers across lifecycle stages, enabling tailored retention strategies
- Repeat buyers demonstrate distinct subscription patterns that can inform loyalty program design

**Revenue Optimization**
- Age group analysis identifies which demographic segments contribute most to revenue
- Gender-based revenue comparison guides targeted marketing investments

**Pricing & Promotion Strategy**
- High-value discount users present opportunities for tiered pricing strategies
- Product-level discount analysis helps optimize promotional calendars while protecting margins

**Product Strategy**
- Top-rated products serve as anchors for marketing campaigns and cross-selling opportunities
- Category-specific bestsellers inform inventory management and merchandising decisions

**Subscription Model Performance**
- Spending pattern differences between subscribers and non-subscribers quantify subscription program ROI
- Correlation between purchase frequency and subscription status reveals conversion opportunities

## Business Recommendations

**Enhance Subscription Value Proposition**
- Promote exclusive benefits and early access to drive subscription adoption among high-frequency purchasers

**Implement Tiered Loyalty Program**
- Design reward structures that incentivize progression from Returning to Loyal segments
- Create personalized offers based on purchase history and spending patterns

**Optimize Discount Strategy**
- Balance promotional intensity to boost volume while maintaining healthy margins
- Focus discounts on customer acquisition rather than high-value repeat purchasers

**Strategic Product Positioning**
- Feature top-rated and best-selling products prominently in marketing campaigns
- Use category insights to optimize product bundling and cross-sell strategies

**Targeted Marketing Campaigns**
- Concentrate marketing spend on high-revenue age groups and demographics
- Develop specialized campaigns for express shipping users who demonstrate higher purchase urgency

## Installation & Setup

```bash
# Install required Python packages
pip install pandas psycopg2-binary sqlalchemy

# PostgreSQL database setup
# Create database 'customer_analysis'
# Update connection credentials in Python script
```

## Usage

1. **Data Preparation:** Run Python notebook to clean data and load into PostgreSQL
2. **Analysis:** Execute SQL queries in PostgreSQL to generate business insights
3. **Visualization:** Open Power BI dashboard for interactive exploration

## Project Structure

```
├── customer_shopping_behavior.csv
├── customer_analysis.ipynb
├── customer_behaviour.sql
├── customer_sales_dashboard.pbix
└── README.md
```

## Future Enhancements

- Implement predictive modeling for customer churn and lifetime value
- Add time-series analysis for seasonal purchasing patterns
- Develop recommendation engine based on purchase history and ratings
- Integrate real-time data pipeline for continuous monitoring
