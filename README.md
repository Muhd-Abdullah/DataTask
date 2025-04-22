# Data Warehouse Design

This repository documents the design, implementation, and architecture of a Data Vault based data warehouse integrating data from sales, order management, and freight systems. It includes end-to-end data modeling—from raw ingestion to business-ready InfoMarts—for analytics use cases such as sales performance, customer insights, and logistics tracking.

## Overview

The project is divided into two main domains:

### Task 1: Data Vault & Reporting Model
- **Implements a Raw Vault** with Hubs, Links, and Satellites for sales transactions
- **Business Vault** layer pivots and enriches KPI metrics (Quantity, TNS, TGS)
- **Dimensional Model** (Star Schema) enables BI-friendly reporting
- Includes SQL scripts for schema creation and transformation logic

### Task 2: Order & Delivery Integration Model
- **Integrates internal order systems with freight feedback**
- Addresses real-world challenges: late-arriving data, SCD, PIT tables, timezone mismatches
- Flow includes Staging → Raw Vault → Business Vault → InfoMart
- Designs fact tables for delivery performance, material movement, and order analysis

## Key Features
- Data Vault methodology: scalable, auditable, and extensible
- Dimensional models for efficient querying (Fact & Dimension tables)
- PIT tables and SCD logic for historization
- Robust handling of semi-structured and late-arriving data
- ETL orchestration & monitoring strategy outlined

## Use Cases
- Sales KPI tracking (Quantity, TGS, TNS)
- Customer and product performance
- Delivery delay and freight analysis
- Historical and real-time snapshot support

## Files
- `Task1.md`: Sales vault schema, SQL, rationale, and dimensional modeling
- `Task2.md`: Order-to-delivery integration, challenges, and vault-to-InfoMart pipeline

## Notes
- Business rules and open questions listed to support future enhancements
- Visual flow diagrams available in both documents for architecture clarity

---

For a deeper dive, refer to the individual markdown files above.
