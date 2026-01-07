# Project-Brazilian-Ecommerce

Enterprise Data Engineering Platform using Azure Medallion Architecture

#Executive Summary
This project implements an enterprise-grade data engineering platform for Brazilian E-commerce (OLIST) data using Microsoft Azure services. The solution follows the Medallion Architecture (Bronze, Silver, Gold) to enable scalable ingestion, enrichment, transformation, and analytics-ready data delivery.

#Architecture Overview
Data is ingested from HTTP (GitHub) and SQL sources using Azure Data Factory and stored in Azure Data Lake Storage Gen2. Azure Databricks performs distributed transformations and enrichment before curated datasets are served through Azure Synapse for business intelligence and analytics.

#Medallion Architecture
Bronze Layer: Raw data stored exactly as received for audit and replay.
Silver Layer: Cleansed and enriched data with standardized formats and language translation.
Gold Layer: Business-ready, analytics-optimized datasets for reporting and insights.

#Data Enrichment
Product category attributes are enriched using MongoDB reference tables. Spanish and Portuguese category names are translated to English, improving global usability and analytical clarity.

#Technology Stack

Azure Data Factory, Azure Data Lake Storage Gen2, Azure Databricks, MongoDB, Azure Synapse Analytics, Power BI / Tableau / Fabric, Python, PySpark.
#Business Value

The platform delivers analytics-ready data, supports scalable processing, enables multilingual enrichment, and aligns with enterprise cloud data engineering best practices.
