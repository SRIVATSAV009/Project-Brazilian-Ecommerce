Enterprise Data Engineering Platform using Azure Medallion Architecture

🎯 Overview

Enterprise-grade data engineering platform built on Microsoft Azure

Designed for scalable ingestion, enrichment, transformation, and analytics delivery

Implements Medallion Architecture (Bronze, Silver, Gold)

Supports multilingual data enrichment for global analytics

Optimized for BI, reporting, and downstream data consumption

🏗️ Architecture Overview
Data Flow

HTTP / SQL Data Sources

Azure Data Factory

Azure Data Lake Storage Gen2 (Bronze)

Azure Databricks

Azure Data Lake Storage Gen2 (Silver and Gold)

Azure Synapse Analytics

BI Tools (Power BI, Tableau, Microsoft Fabric)

Reference Enrichment Flow

MongoDB

Azure Databricks

🥉 Bronze Layer – Raw Data

Stores source data exactly as received

No transformations or schema enforcement

Supports replay, auditing, and traceability

Technologies

Azure Data Factory

Azure Data Lake Storage Gen2

🥈 Silver Layer – Cleansed and Enriched Data

Applies data quality and standardization rules

Normalizes data types and handles null values

Removes duplicates where applicable

Enriches datasets using reference lookups

Translates product categories from Spanish/Portuguese to English

Technologies

Azure Databricks (Apache Spark)

MongoDB (reference and translation store)

🥇 Gold Layer – Analytics Ready Data

Curated, business-aligned datasets

Stable schemas designed for analytics

Optimized for query performance

Consumers

Azure Synapse Analytics

Power BI

Tableau

Microsoft Fabric

Downstream APIs and ML workloads

🌍 Data Enrichment Strategy

Reference data stored in MongoDB

Translation mappings maintained for product categories

Databricks joins transactional data with reference data

Enriched attributes persisted in Silver and Gold layers

Enables consistent, global-ready analytics dimensions

⚙️ Core Platform Components
Azure Data Factory

Orchestrates ingestion pipelines

Handles HTTP and SQL-based sources

Populates the Bronze layer

Azure Data Lake Storage Gen2

Centralized storage for Bronze, Silver, and Gold layers

Secure and scalable data storage

Azure Databricks

Executes distributed transformations

Applies cleansing and enrichment logic

Writes curated datasets back to ADLS

MongoDB

Stores reference and translation datasets

Supports enrichment during Silver processing

Azure Synapse Analytics

Provides analytical query layer

Serves Gold datasets to BI tools

🧰 Technology Stack

Azure Data Factory

Azure Data Lake Storage Gen2

Azure Databricks (Apache Spark)

MongoDB

Azure Synapse Analytics

Power BI

Tableau

Microsoft Fabric

Python

PySpark

✅ Key Outcomes

Production-aligned Medallion Architecture implementation

Scalable ingestion and transformation pipelines

Multilingual data enrichment capability

Analytics-ready datasets

Cloud-native and extensible platform design
