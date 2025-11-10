# nyc-taxi-azure-data-engineering-project
This project demonstrates an end-to-end data engineering pipeline built on the Azure ecosystem. The pipeline ingests raw data from an API source, processes it using Azure Data Factory (ADF), transforms it using Databricks (PySpark), and stores it efficiently in Azure Data Lake Gen2 using the Medallion Architecture — Bronze, Silver, and Gold layers.

## NYC Taxi Data
The dataset contains NYC taxi trip records with fields such as:

- VendorID, tpep_pickup_datetime, tpep_dropoff_datetime, passenger_count, trip_distance  
- pickup_longitude, pickup_latitude, dropoff_longitude, dropoff_latitude, RateCodeID  
- payment_type, fare_amount, total_amount, and more...

## Architecture Components

- **Source:** API providing taxi trip data.
- **Ingestion:** Azure Data Factory used to extract and load raw data into the Bronze layer. 
- **Storage:** Azure Data Lake Storage Gen2 for scalable, secure data storage.  
- **Transformation:** Databricks used for data cleaning, transformation, and aggregation.

## Workflow

- **Data Ingestion — Azure Data Factory:**  
  Built a parameterized pipeline to handle multiple data sources dynamically.  
  Parameters include:  
  - `source_url` (API endpoint)  
  - `file_name` (naming convention for output)  
  - `target_path` (Bronze folder destination)  
  ADF uses these parameters to ingest data into the Bronze layer in Parquet format.   

- **Data Transformation — Azure Databricks:**  
  Performed multi-layer transformations using Spark notebooks.  
  - **Bronze → Silver:** Data cleaning, schema enforcement, and null-handling.  
  - **Silver → Gold:** Aggregations, joins, and business logic for reporting.  
  Transformed data is stored back into Azure Data Lake Gen2 as Parquet (Silver) and Delta (Gold) formats.  

- **Data Serving — Delta Lake:**  
  The Gold layer leverages Delta Lake for:  
  - ACID transactions  
  - Time travel and schema evolution  
  - Optimized performance for analytics  
  Ready for visualization tools such as Power BI or Synapse Serverless SQL.

## Outcome

- **Automated Pipeline:**  
  A fully automated and parameterized data pipeline capable of handling dynamic ingestion, transformation, and storage of both structured and semi-structured data efficiently.

- **Optimized Gold Layer:**  
  The final output (Gold layer) is queryable, reliable, and optimized for BI and analytics workloads.

- **Modern Lakehouse Implementation:**  
  Represents a modern **Lakehouse architecture** on Azure using **ADF**, **Databricks**, **Delta Lake**, and **Power BI** for end-to-end data engineering and analytics.



