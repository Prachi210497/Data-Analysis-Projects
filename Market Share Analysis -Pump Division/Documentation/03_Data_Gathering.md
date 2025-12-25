# 03. Data Gathering

## 1. Purpose of This Document

This document outlines the **data sources, ownership, structure, and granularity** used in the Market Share Analysis project. It ensures transparency on where data originates from and how it supports business requirements.

---

## 2. Overview of Data Sources

The analysis is built by consolidating data from multiple operational datasets related to sales, installed base, and service ownership.

2.1 Internal Data Sources
| Source System            | Description                                    | Key Usage                                 |
| ------------------------ | ---------------------------------------------- | ----------------------------------------- |
| CRM System               | Customer, opportunity, and sales pipeline data | Customer segmentation, deal conversion    |
| SAP / ERP                | Billing, invoicing, product-level revenue      | Revenue calculation, YoY comparison       |
| Installed Base (IB) Data | Installed equipment and service contracts      | Market penetration and opportunity sizing |
| Sales Master Data        | Sales hierarchy, regions, territories          | Regional and salesperson performance      |
| MALP List                | Product, Model and its price list              | Evaluate potential  

Note: External data was used only for reference and validation, while all KPI calculations were driven by internal systems.

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

Represents pumps installed at customer locations along with their lifecycle and Pump operational status.

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

A bridge table used to resolve **One-to-many relationships** between pumps and service personnel.

### Key Attributes

* Pump ID
* Service Person Name / ID

### Granularity

* **Pump-to-sales-person mapping**

### Business Relevance

* Enables sales-person-wise analysis
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

## 10. Data Confidentiality & Professional Ethics

The documentation and explanations shared in this project are intended to demonstrate my role, approach, and analytical thinking as a Business Analyst.

To maintain the trust of the organization and comply with company policies and confidentiality agreements, the following practices were strictly followed:

No actual company data, reports, or internal files are shared in this repository

All examples, structures, and explanations are generic and anonymized

Sensitive business metrics, customer information, and financial figures are masked or excluded

The Power BI files and datasets used internally are not uploaded or publicly shared

To comply with organizational policies, the data displayed is anonymized and representative, ensuring confidentiality while accurately reflecting the business logic used for analysi

This project reflects how I work, how I think, and how I approach problem-solving, while fully adhering to organizational rules, data privacy, and professional ethics.

## 11. Output of Data Gathering Phase

The outcome of this phase is a **consolidated, well-understood dataset landscape** ready for transformation, modeling, and analytics.
