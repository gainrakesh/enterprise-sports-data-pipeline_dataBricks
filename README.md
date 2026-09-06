# FMCG Data Engineering Project – Sports Bar

## Project Overview

Atlikon is an FMCG company that sells sports-related products and already has a good data pipeline and data warehouse.

Atlikon acquired another company called **Sports Bar (SB)**, which sells sports-related healthy drinks and other products. Previously, SB mainly used Excel files to analyze their data and did not have a proper data warehouse.

I built an **end-to-end data pipeline for Sports Bar** using Databricks.

The main goal was to ingest the SB data, process it using a **Bronze, Silver, and Gold architecture**, and finally combine the SB Gold data with Atlikon's existing Gold layer.

## Architecture

The pipeline follows a simple **Medallion Architecture**:

**Databricks Volume → Bronze → Silver → Gold → Parent Company Gold**

### Data Flow

1. Historical SB data is loaded initially using a **full load**.
2. New data coming into the landing folder is processed automatically.
3. Raw data is ingested into the Bronze layer.
4. Data is cleaned and transformed in the Silver layer.
5. Business-ready data is created in the Gold layer.
6. SB Gold data is combined with Atlikon's existing Gold data.
7. SQL views are created by joining the required fact and dimension tables.
8. Genie was used to create charts for data analysis.

## Data Source

The data is stored in **Databricks Volumes**.

For order data, I created two folders:

* `landing` – New files are placed here.
* `processed` – Files are moved here after successful processing.

After the file is processed, it is removed from the landing folder and moved to the processed folder.

## Tables

### Fact Table

* **Orders**

### Dimension Tables

* **Customer**
* **Products**
* **Prices**

These tables are processed through the different layers and finally used to create the Gold layer.

## Full Load and Incremental Processing

Initially, I performed a **full load** because Sports Bar already had historical data that needed to be loaded into the new data platform.

After the initial load, the pipeline is designed to process **new incoming data automatically**.

So the overall process is:

**Historical Data → Full Load**

**New Data → Automatically Ingest and Process**

This allows the Gold layer to stay updated as new data arrives.

## Technologies Used

* Databricks
* PySpark
* SQL
* Delta Lake
* Databricks Volumes
* Medallion Architecture
* Genie

## Key Implementation

The main things implemented in this project are:

* End-to-end data pipeline
* Full historical data load
* Automatic processing of new data
* Bronze, Silver and Gold layers
* Fact and dimension tables
* File movement from landing to processed
* Data transformation using PySpark and SQL
* Combining SB Gold data with Atlikon Gold data
* SQL views for analysis
* Data visualization using Genie

## Final Outcome

The project provides Sports Bar with a proper data pipeline and structured data platform instead of depending mainly on Excel for analysis.

The processed SB data can also be integrated with Atlikon's existing Gold data, which provides a common view of the business data for further analysis and reporting.

