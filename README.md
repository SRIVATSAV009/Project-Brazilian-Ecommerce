# Project-Brazilian-Ecommerce
Enterprise Data Engineering Platform Using Medallion Architecture on Azure

Overview

This repository implements an enterprise-grade data engineering architecture designed to ingest, enrich, transform, and serve Brazilian E-commerce (OLIST) data using Azure-native services and the Medallion Architecture (Bronze, Silver, Gold) pattern.

The platform supports:

Batch ingestion from HTTP (GitHub) and SQL sources

Scalable storage using Azure Data Lake Storage Gen2

Distributed transformations using Azure Databricks

Data enrichment using MongoDB reference tables

Analytics serving through Azure Synapse

Business intelligence consumption via Power BI / Tableau / Microsoft Fabric

The architecture is aligned with modern lakehouse and enterprise analytics standards.

High-Level Architecture
Data Sources
(HTTP / SQL)
     |
     v
Azure Data Factory
     |
     v
ADLS Gen2 — Bronze (Raw Data)
     |
     v
Azure Databricks
(Data Transformation + Enrichment)
     |
     v
ADLS Gen2 — Silver / Gold
     |
     v
Azure Synapse Analytics
     |
     v
Visualization
(Power BI / Tableau / Fabric)


Enrichment Source

MongoDB
(Product Category Translation & Reference Data)
        |
        v
Azure Databricks

Medallion Architecture Implementation
Bronze Layer — Raw Data

Purpose

Capture source data exactly as received

Enable reprocessing, traceability, and auditability

Implementation

Azure Data Factory ingests data from:

HTTP endpoints (GitHub raw CSV files)

SQL tables (if applicable)

Data is written unchanged to ADLS Gen2 (Bronze container)

Characteristics

No schema enforcement

No transformations

Append-only storage

Silver Layer — Cleansed & Enriched Data

Purpose

Improve data quality

Apply enrichment and standardization

Transformations

Data type normalization

Null handling and cleansing

Deduplication logic

Data enrichment via MongoDB

Product category reference lookup

Spanish → English translation for category names

Standardized naming for downstream analytics

Technology

Azure Databricks (Apache Spark)

MongoDB used as a lookup and enrichment store

Output

Cleaned and enriched datasets written to ADLS Gen2 Silver layer

Gold Layer — Analytics-Ready Data

Purpose

Serve business-ready datasets optimized for analytics

Provide a stable semantic layer for BI and reporting

Characteristics

Curated schemas

Business-aligned tables

Optimized for analytical queries

Consumers

Azure Synapse Analytics

Power BI

Tableau

Microsoft Fabric

Downstream APIs and ML pipelines

Data Enrichment Strategy
Use Case: Language Translation (Spanish → English)

Certain product category attributes are provided in Spanish/Portuguese and are not suitable for global analytics.

Approach

MongoDB maintains a reference table mapping:

Source category name

English translation

Azure Databricks joins transactional data with MongoDB reference data

Enriched attributes are persisted in Silver and Gold layers

Outcome

Improved interpretability

Standardized dimensions for analytics and reporting

Technology Stack

Cloud Platform: Microsoft Azure

Ingestion & Orchestration: Azure Data Factory

Storage: Azure Data Lake Storage Gen2

Processing & Transformation: Azure Databricks (Spark)

Enrichment Store: MongoDB

Analytics Engine: Azure Synapse Analytics

Visualization: Power BI, Tableau, Microsoft Fabric

Programming Language: Python / PySpark

Version Control: GitHub

Repository Structure
Project-Brazilian-Ecommerce/
│
├── Data/
│   ├── bronze/
│   ├── silver/
│   └── gold/
│
├── ingestion/
│   └── adf_http_ingestion_config.md
│
├── transformation/
│   └── databricks_silver_gold_transformations.py
│
├── enrichment/
│   └── mongodb_category_translation.py
│
├── analytics/
│   └── synapse_views.sql
│
├── architecture/
│   └── architecture_diagram.png
│
└── README.md

Azure Data Factory Pipeline Design
Linked Services

HTTP Linked Service (GitHub ingestion)

Azure Data Lake Storage Gen2

Azure Databricks

SQL (optional source integration)

Pipeline Capabilities

Parameterized ingestion using ForEach activities

Dynamic dataset handling

Fault-tolerant batch ingestion

Separation of Bronze and downstream layers

Azure Databricks Processing

Responsibilities

Read raw data from Bronze

Apply cleansing and normalization

Perform MongoDB-based enrichment

Write Silver and Gold datasets back to ADLS

Design Principles

Idempotent transformations

Schema evolution handling

Scalable Spark execution

Azure Synapse & Analytics

Gold-layer datasets are exposed to Azure Synapse for:

Analytical querying

Aggregations

Reporting views

These datasets are then consumed by BI tools such as Power BI, Tableau, and Fabric.

Key Outcomes

Demonstrates real-world Medallion Architecture implementation

Integrates batch ingestion, enrichment, and analytics

Uses Azure-native, enterprise-grade services

Supports scalable analytics and reporting workloads

Designed for extensibility and production readiness
