# Data Model Documentation

This documentation describes the design and implementation of a data warehouse that integrates data from order management and freight forwarding systems. The objective is to create a robust data model that supports analytical use cases such as sales analysis, customer behavior, and logistics performance.

---

## Table of Contents

- [Data Model Documentation](#data-model-documentation)
  - [Table of Contents](#table-of-contents)
  - [Implementation and Decision Rationale](#implementation-and-decision-rationale)
  - [Flow Diagram](#flow-diagram)
      - [Source System](#source-system)
      - [Staging Area](#staging-area)
      - [Raw and Business Vault](#raw-and-business-vault)
      - [InfoMart](#infomart)

## Implementation and Decision Rationale

## Flow Diagram

This flow diagram illustrates the end-to-end data pipeline, from source systems to business intelligence-ready InfoMarts, using a Data Vault approach.

![Flow Diagram](image-1.png)

#### Source System

Data originates from:

  - Internal databases or systems

  - Excel spreadsheets

  - FTP server from the freight forwarder (daily delivery feedback)

All raw data is first loaded into the staging area, which serves as the input for the data vault model.

#### Staging Area

The Staging Layer is a transient zone where raw data from all source systems is ingested, cleaned, and prepared for loading into the Raw and Business Vault. This layer maintains the source structure and enables auditing.

#### Raw and Business Vault

The core of the Data Vault is split into:

- **HUBs** – Capture business keys like *Customer*, *Order*, *Delivery*, *Material*

- **LINKs** – Capture relationships such as:

    - *Order_Customer*

    - *Order_Delivery*

    - *Order_Material*

    - *Delivery_Customer*

- **SATELLITES** – Capture descriptive attributes and history, such as:

    - *Customer*

    - *Order_Header*

    - *Order_Line*

    - *Delivery_Header*

    - *Material*

    - *Truck_Feedback*

This structure enables full historical tracking, data lineage, and scalability.

#### InfoMart

The InfoMart transforms the vault structure into business-friendly dimensional models (star schemas), facilitating reporting, dashboards, and self-service BI.

- **FACT Tables**
  
    - *FactSales* – Sales transactions by item and customer

    - *FactDeliveryPerformance* – Delivery punctuality, matched with truck feedback

    - *FactOrder* – Summary of orders by customer/date

    - *FactMaterial* – Material usage and delivery data

- **Dimension Tables**

    - *DimCustomer*

    - *DimMaterial*

    - *DimOrder*

    - *DimDelivery*

    - *DimDate*

These fact and dimension tables are joined to support use cases such as:

1. Best-selling items

2. Customer performance

3. Delivery delays

4. Average sales price per product