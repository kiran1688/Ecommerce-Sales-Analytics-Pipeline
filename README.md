# E-commerce Sales Analytics Pipeline

 ## Project Overview

The E-commerce Sales Analytics Pipeline is an end-to-end Data Engineering project designed to process raw transactional data from an e-commerce marketplace and transform it into analytics-ready datasets for reporting and business insights.

The pipeline follows the Medallion Architecture (Bronze → Silver → Gold) using the Databricks Lakehouse platform. Raw data is ingested from AWS S3, processed using PySpark, stored in Delta Lake tables, and structured into a Star Schema model for analytics.

This system enables organizations to analyze sales performance, customer behavior, and product trends efficiently.

---

## Project Objectives

## 🎯 Project Objectives

- The goal of this project is to build a *scalable, reliable, and production-ready batch ETL pipeline* for e-commerce sales analytics capable of handling large volumes of data efficiently.

- The pipeline is designed to ensure *high data quality, fault tolerance, and consistency*, enabling trusted and accurate data for business decision-making.

- It aims to deliver *analytics-ready datasets using a structured data model*, supporting efficient querying and performance optimization.

- The project focuses on generating *actionable business insights* such as sales trends, customer behavior, and product performance.

- It also emphasizes *end-to-end automation and monitoring*, ensuring smooth, scheduled, and reliable pipeline execution.

---

## Lakehouse Architecture

The pipeline follows a modern Lakehouse Data Engineering Architecture.



![object_remover-1773815864000](https://github.com/user-attachments/assets/1eff00c1-4bec-42e3-8162-ce8b6e37844d)

---

## Technology Stack

| Technology | Purpose |
|------------|--------|
| AWS S3 | Data Lake Storage |
| Databricks | Data Engineering Platform |
| PySpark | Distributed Data Processing |
| Delta Lake | Optimized Storage Format |
| Unity Catalog | Metadata Management |
| SQL | Analytical Queries |
| Databricks Workflows | Pipeline Scheduling |
| Git | Version Control |
| dbt | Advanced Data Transformations |

---

## Dataset

Dataset Used:

Brazilian E-Commerce Public Dataset (Olist) from Kaggle.

The dataset contains transactional information related to:

- Customers
- Orders
- Order Items
- Payments
- Products
- Sellers
- Product Categories

Example Raw Storage Path:
s3://ecommerce-data-lake/raw/ecommerce_sales/YYYY/MM/DD/


---

## Data Pipeline Layers

### Bronze Layer – Raw Data Ingestion

Purpose:
Store raw data in Delta format.

Tasks performed:

- Read CSV datasets from AWS S3
- Convert raw data into Delta tables
- Preserve original data with minimal transformation
- Add ingestion metadata

Example Bronze Tables:
| Bronze Tables |
|---------------|
| bronze_customers |
| bronze_orders |
| bronze_order_items |
| bronze_payments |
| bronze_products |
| bronze_sellers |



---

### Silver Layer – Data Cleaning and Transformation

*Purpose:*  
Create clean and standardized datasets.

*Transformations include:*

- Remove duplicate records  
- Handle missing values  
- Convert timestamp formats  
- Standardize column formats  
- Perform data validation checks  
- Join related datasets  
- Apply data type casting  
- Add metadata columns (processed_timestamp, data_quality_flag)  

---

*Example Silver Tables:*

| Silver Tables |
|---------------|
| customers |
| orders |
| order_items |
| payments |
| products |
| product_category_translation |
| sellers |

---

### Gold Layer – Analytics Data Model

*Purpose:*  
Create an analytics-ready star schema for business intelligence.

| Table Type   | Table Name     |
|-------------|----------------|
| Fact Table  | fact_orders    |
| Fact Table  | fact_payments  |
| Fact Table  | fact_sales     |
| Dimension   | dim_customers  |
| Dimension   | dim_products   |
| Dimension   | dim_sellers    |
| Dimension   | dim_date       |

---

The Gold layer supports analytical queries such as revenue analysis, customer behavior analysis, and seller performance evaluation.
---

##  Business Insights Generated

The pipeline generates business-ready insights from the Gold layer, structured into three key dashboards.

---

###  Sales Performance Insights

- Revenue Trend Analysis (Daily / Monthly)
- Total Orders and Sales Volume
- Top Selling Products by Revenue
- Sales by Product Category
- Customer Distribution by Region


---

###  Customer Analytics Insights

- Customer Purchase Frequency
- Average Order Value (AOV)
- Seller Performance Analysis
- Delivery Performance
- Shipping Cost Impact on Revenue


---

###  Strategic Insights

- Customer Lifetime Value (CLV)
- Customer Segmentation
- Product Affinity (Market Basket Analysis)
- Demand Forecasting (Historical Trend)
- Customer Churn Identification


---

##  Analytics Dashboards

The Gold layer supports multiple business dashboards designed for different stakeholders.

---

###  Sales Performance Dashboard

*Key Metrics:*
- total_revenue
- Total_orders 
- Top Selling Products 
- Revenue Trend 
- Sales by Region

<img width="1017" height="758" alt="Sales Performance" src="https://github.com/user-attachments/assets/b5f04fd3-eab9-41e8-b066-958ad4f127bd" />

-----

###  Customer Analytics Dashboard

*Key Metrics:*

- Customer Purchase Frequency
- Repeat vs One-Time Customers
- Average Order Value by Customer
- Top Customers by Revenue
- Top Customers by Revenue 

<img width="1017" height="749" alt="Customer Analysis" src="https://github.com/user-attachments/assets/a973f674-c522-4a54-9508-40c8a7a2415b" />

----

###  Strategic Insights Dashboard

*Key Metrics:*

- Seller Performance
- Delivery Performance
- Shipping Cost Impact

<img width="1154" height="509" alt="Strategic Insights" src="https://github.com/user-attachments/assets/94dd2ebb-3a02-458c-8d2a-4d9c136fb5a9" />

----

##  Pipeline Automation

The pipeline execution is automated using *Databricks Workflows and AWS Airflow* to ensure reliable and scheduled processing.

*Schedule:*  
Daily Batch Job  
Time: 3 AM UTC  

*Workflow Design:*

- Created a *Databricks Job* where each notebook is configured as an individual task:
  - Bronze ingestion notebook  
  - Silver transformation notebook  
  - Gold modeling notebook  
  - Data validation and quality checks  

- Defined task dependencies to ensure proper execution order across layers.

- Integrated *AWS Airflow* to orchestrate the Databricks job:
  - Airflow triggers the Databricks workflow  
  - Manages scheduling and pipeline execution  
  - Ensures end-to-end orchestration across all stages  

- Configured *Slack alerts* for real-time notifications:
  - Job success/failure alerts  
  - Data quality issue alerts  
  - Pipeline failure monitoring  

---

*Workflow tasks include:*

1. Data ingestion from AWS S3 (Raw Zone)  
2. Bronze layer creation (Delta tables)  
3. Silver layer transformation (data cleaning, validation, quarantine handling)  
4. Gold layer modeling (Star Schema )  
5. Data quality checks and validation  
6. Analytics table preparation for dashboards  

---

##  Data Quality and Monitoring

The pipeline implements strong *data quality and monitoring mechanisms* to ensure reliability and accuracy.

*Data Quality Checks:*

- Record count validation  
- Schema validation  
- Null value handling and checks  
- Duplicate detection  
- Data validation rules (invalid/malformed data detection)  

*Monitoring & Logging:*

- Errors and pipeline issues are logged in:
  logs.etl_errors  

- Alerts are triggered for:
  - Job failures  
  - Data quality issues  
  - Pipeline anomalies  

---

##  Key Project Outcomes

- Built a *scalable lakehouse data pipeline* using AWS S3 and Databricks  
- Implemented *Medallion Architecture (Bronze, Silver, Gold)* for structured data processing  
- Developed *robust data quality framework* with validation and quarantine handling  
- Designed an *analytics-ready Star Schema model* with SCD Type 2 implementation  
- Enabled *business-ready insights and dashboards* for analytics use cases  
- Automated the pipeline using *Databricks Workflows and Airflow* for reliable execution  

---

##  Future Improvements

- Integrate *real-time streaming ingestion* using Spark Structured Streaming  
- Enhance analytics with *advanced forecasting and ML models*  
- Deploy dashboards using *Power BI / Databricks SQL dashboards*  
- Implement *CI/CD pipelines* for automated testing and deployment  
- Add *data lineage and governance* using Unity Catalog enhancements  

---

## Conclusion

This project demonstrates how a modern data engineering pipeline can transform raw e-commerce data into reliable analytics datasets and business insights using the Lakehouse architecture.

The system integrates AWS S3, Databricks, PySpark, Delta Lake, and SQL analytics to deliver scalable and efficient data processing for business intelligence.
