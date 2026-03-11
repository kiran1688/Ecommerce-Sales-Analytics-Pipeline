# Ecommerce-Sales-Analytics-Pipeline

**Project Overview**

The Ecommerce Sales Analytics Pipeline is a data engineering project that processes raw ecommerce data and transforms it into structured datasets for analytics and reporting.
The pipeline follows a Medallion Architecture (Bronze, Silver, Gold layers) to clean, transform, and analyze ecommerce datasets.
The project is implemented using PySpark and SQL on the Databricks platform to build a scalable data pipeline.

**Architecture**
The pipeline follows three layers:

Bronze Layer (Raw Data)
* Raw CSV files are ingested into the Bronze layer.
* Data is stored in its original format.
* No transformations are applied.


Silver Layer (Cleaned Data)
* Data cleaning and transformation are applied.
* Handling NULL values
* Removing special characters
* Datatype conversion
* Standardizing columns.

Gold Layer (Business Analytics)
* Aggregated datasets are created for analytics.
* Business insights are generated for reporting and dashboards.


Datasets Used

The project uses multiple ecommerce datasets:
products_dataset.csv
orders_dataset.csv
order_payments_dataset.csv
customers_dataset.csv
sellers_dataset.csv
Key columns include product details, order information, payment details, seller information, and customer data.


Technologies Used

* Python
* PySpark
* SQL
* Databricks
* Delta Lake
* Git & GitHub


Data Processing Steps

1. Data Ingestion
-Raw CSV files are loaded into Databricks using PySpark.
2. Data Cleaning
-The following checks are performed:
-NULL value detection
-Special character validation
-String validation in date columns
3. Data Transformation
-Datatype conversion
-Column standardization
-Data formatting
4. Data Storage
-Processed datasets are stored as Delta Tables for better performance and scalability.

Business Insights
* The analytics layer can answer business questions such as:
* Total sales by product category
* Top performing sellers
* Customer purchase trends
* Payment installment patterns
* Delivery performance analysis


Project Structure

                                                  Ecommerce-Sales-Analytics-Pipeline
                                                  │
                                                  ├── data
                                                  │   ├── products_dataset.csv
                                                  │   ├── orders_dataset.csv
                                                  │   ├── order_payments_dataset.csv
                                                  │   ├── customers_dataset.csv
                                                  │   └── sellers_dataset.csv
                                                  │
                                                  ├── notebooks
                                                  │   ├── bronze_ingestion.py
                                                  │   ├── silver_cleaning.py
                                                  │   └── gold_analytics.py
                                                  │
                                                  ├── sql
                                                  │   └── business_queries.sql
                                                  │
                                                  └── README.md


Future Improvements
* Build interactive dashboards using Power BI or Tableau
* Implement workflow orchestration
* Add real-time streaming ingestion
* Deploy pipeline using CI/CD

