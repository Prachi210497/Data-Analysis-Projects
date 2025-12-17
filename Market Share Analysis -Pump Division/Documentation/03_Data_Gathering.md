# 03. Data Gathering

## 1. Purpose of This Document

This document outlines the **data sources, ownership, structure, and granularity** used in the Market Share Analysis project. It ensures transparency on where data originates from and how it supports business requirements.

---

## 2. Overview of Data Sources

The analysis is built by consolidating data from multiple operational datasets related to sales, installed base, and service ownership.

| Data Source                     | Description                                 | Business Use                          |
| ------------------------------- | ------------------------------------------- | ------------------------------------- |
| Order Booking (OB Data)         | Sales and order-related information         | Revenue, customer value, market share |
| Installed Base (IB Data)        | Installed pump and status details           | Operational, inactive, and lost pumps |
| Service Person Mapping (Bridge) | Mapping between pumps and service personnel | Service-wise performance & RLS        |
| Calendar Table                  | Standard date dimension                     | Time-based analysis                   |

---

## 3. Order Booking (OB Data)

### Description

Contains sales and order-related data representing commercial transactions with customers.

### Key Attributes (Indicative)

* Customer Name
* Customer ID
* Order Value (INR)
* Order Date / Year
* Sales Region / State
* Product / Pump Reference

### Granularity

* **Customer-level** and **order-level** data

### Business Relevance

* Used to calculate **Total Value (INR)**
* Supports customer-wise and region-wise analysis

---

## 4. Installed Base (IB Data)

### Description

Represents pumps installed at customer locations along with their lifecycle and operational status.

### Key Attributes (Indicative)

* Pump ID
* Customer Name
* Pump Status (Operational / Inactive / Lost)
* Installed Year
* Potential Value

### Granularity

* **Pump-level** data

### Business Relevance

* Used to track **operational, inactive, and lost pumps**
* Forms the base for **potential value and cumulative analysis**

---

## 5. Service Person Mapping (Bridge Table)

### Description

A bridge table used to resolve **many-to-many relationships** between pumps and service personnel.

### Key Attributes

* Pump ID
* Service Person Name / ID

### Granularity

* **Pump-to-service-person mapping**

### Business Relevance

* Enables service-person-wise analysis
* Supports **Row-Level Security (RLS)** implementation

---

## 6. Calendar Table

### Description

A standard date dimension table created to support consistent time intelligence.

### Key Attributes

* Date
* Year
* Month
* Year-Month

### Business Relevance

* Enables year-wise and trend analysis
* Used across all fact tables

---

## 7. Data Ownership & Refresh

| Dataset        | Owner                | Refresh Type     |
| -------------- | -------------------- | ---------------- |
| OB Data        | Business / Sales Ops | Periodic (Batch) |
| IB Data        | Service Ops          | Periodic (Batch) |
| Mapping Tables | Analytics Team       | As required      |

---

## 8. Data Quality Considerations

* Missing or blank customer names
* Inconsistent pump status values
* Duplicate pump records across years
* Date format inconsistencies

(Data handling and resolution steps are covered in `04_Data_Preprocessing.md`)

---

## 9. Assumptions

* Source systems provide accurate and approved data
* Pump IDs uniquely identify installed units
* OB and IB data can be linked via customer references

---

## 10. Output of Data Gathering Phase

The outcome of this phase is a **consolidated, well-understood dataset landscape** ready for transformation, modeling, and analytics.

---

*Next Document: `04_Data_Preprocessing.md`*
