# Retail Data Engineering Pipeline

An end-to-end retail data engineering project built using Microsoft Azure.  
The project ingests retail data from multiple sources, stores it in Azure Data Lake Storage Gen2, processes it using Azure Databricks and PySpark, and creates analytics-ready datasets for Power BI reporting.

---

## Project Overview

This project demonstrates a complete cloud-based data engineering workflow using the **Medallion Architecture**.

The pipeline processes four main retail datasets:

- Transactions
- Customers
- Products
- Stores

The data flows through the following architecture:

**SQL / API → Azure Data Factory → ADLS Gen2 → Azure Databricks → Bronze → Silver → Gold → Power BI**

---

## Architecture

```text
                 ┌─────────────────────┐
                 │    Data Sources     │
                 │                     │
                 │ Azure SQL / API     │
                 │ Transactions        │
                 │ Customers           │
                 │ Products            │
                 │ Stores              │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │ Azure Data Factory  │
                 │                     │
                 │ Data Ingestion      │
                 │ & Orchestration     │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │     ADLS Gen2       │
                 │                     │
                 │   Bronze Layer      │
                 │    Raw Data         │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │ Azure Databricks    │
                 │      PySpark        │
                 │                     │
                 │ Data Cleaning       │
                 │ Transformation      │
                 │ Joins & Aggregation │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │    Silver Layer     │
                 │                     │
                 │ Cleaned & Joined    │
                 │ Data                │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │     Gold Layer      │
                 │                     │
                 │ Analytics-Ready     │
                 │ Data                │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │      Power BI       │
                 │                     │
                 │ Reporting &         │
                 │ Visualization       │
                 └─────────────────────┘
