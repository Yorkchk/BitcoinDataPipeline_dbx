# ₿ Bitcoin Real-time Price & Market Cap Tracker

##  Project Overview
This project implements a robust, scalable, and fully automated data pipeline to ingest, process, and analyze real-time Bitcoin price and market capitalization data. Leveraging the power of **Azure Databricks**, **Delta Lake**, and **Azure Data Lake Storage Gen2**, this solution provides historical trends and aggregates for analytical insights, following the industry-standard **Medallion Architecture** (Bronze, Silver, Gold layers).

###  Key Technologies Used
* **Azure Databricks:** Unified analytics platform for ETL and data processing.
* **Delta Lake:** Open-source storage layer bringing ACID transactions and schema enforcement.
* **Azure Data Lake Storage Gen2 (ADLS Gen2):** Scalable, secure data lake for storing raw and processed data.
* **PySpark & Structured Streaming:** For incremental, fault-tolerant data ingestion.
* **Spark SQL:** For business-layer transformations and aggregations.
* **CoinGecko API:** External source for real-time Bitcoin data.
* **Databricks Jobs:** For orchestrating and scheduling the end-to-end pipeline.
* **Power BI:** For data visualization and interactive analysis.

---

##  Architecture & Data Flow
The pipeline adheres strictly to the Medallion Architecture, ensuring data quality and reliability across different layers (raw -> bronze -> silver -> gold)



### Flow of Actions:
1. **Streaming Ingestion:** A Databricks Job triggers a PySpark notebook to stream real-time Bitcoin data from CoinGecko.
2. **Bronze Layer Landing:** Raw JSON data is appended to the `bitcoin_raw` Delta table in ADLS Gen2, maintaining schema inference.
3. **Silver Layer Processing:** Data is read from Bronze, cleaned, filtered, and schema-enforced, then loaded incrementally into `bitcoin_silver`.
4. **Gold Layer Aggregation:** Business-level aggregations (e.g., hourly OHLC) are stored in the `bitcoin_gold_hourly_agg` Delta table.
5. 
