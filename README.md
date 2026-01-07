# Project-Brazilian-Ecommerce


Enterprise Data Engineering Platform – Azure Medallion Architecture

Executive Summary

This repository contains an enterprise-style data engineering platform built to ingest, enrich, transform, and serve Brazilian E-commerce (OLIST) data using Azure-native services.
The solution follows the Medallion Architecture (Bronze, Silver, Gold) to ensure data reliability, scalability, and analytics readiness.

The platform supports batch ingestion from HTTP and SQL sources, distributed transformations, reference-based enrichment, and analytics consumption through Synapse and BI tools.

Architecture Overview

HTTP / SQL Sources
        ↓
Azure Data Factory
        ↓
ADLS Gen2 (Bronze)
        ↓
Azure Databricks
        ↓
ADLS Gen2 (Silver / Gold)
        ↓
Azure Synapse Analytics
        ↓
Power BI / Tableau / Fabric

Medallion Architecture Implementation
Bronze Layer – Raw Data

Stores source data exactly as ingested

No transformations or schema enforcement

Supports replay, auditing, and traceability

Technology:
Azure Data Factory, ADLS Gen2

Silver Layer – Cleansed & Enriched Data

Data cleansing and normalization

Deduplication and standardization

Language enrichment using MongoDB

Product categories translated from Spanish/Portuguese to English

Technology:
Azure Databricks (Spark), MongoDB

Gold Layer – Analytics-Ready Data

Curated, business-aligned datasets

Optimized for analytical workloads

Stable schemas for reporting and insights

Consumers:
Azure Synapse, Power BI, Tableau, Microsoft Fabric

Data Enrichment Strategy

Reference data is maintained in MongoDB and joined during Databricks processing to enrich transactional datasets.
This includes Spanish-to-English translation of product categories, enabling global-ready analytics and consistent business dimensions.

Core Platform Components

Azure Data Factory
Orchestrates ingestion from HTTP and SQL sources into the Bronze layer.

Azure Data Lake Storage Gen2
Central storage for Bronze, Silver, and Gold datasets.

Azure Databricks
Performs distributed transformations and enrichment logic.

MongoDB
Provides reference and translation lookup tables.

Azure Synapse Analytics
Serves curated data for analytical queries and BI consumption.

Technology Stack

Azure Data Factory
Azure Data Lake Storage Gen2
Azure Databricks (Apache Spark)
MongoDB
Azure Synapse Analytics
Power BI / Tableau / Microsoft Fabric
Python / PySpark

Outcomes

Production-aligned Medallion Architecture implementation

Scalable ingestion and transformation design

Multilingual data enrichment capability

Analytics-ready datasets for enterprise reporting

Cloud-native, extensible data platform
