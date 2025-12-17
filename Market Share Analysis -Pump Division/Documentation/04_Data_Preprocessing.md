# 04. Data Preprocessing

## 1. Purpose of This Document

This document explains the **data preprocessing and transformation steps** performed using manual intervention and Power Query to prepare raw source data for accurate modeling and analysis. The goal is to ensure **data quality, consistency, and reliability** before applying business logic and DAX measures.

---

## 2. Tools Used

* **Sharepoint - Power BI Desktop – Power Query Editor**

---

## 3. Common Data Issues Identified

During initial data assessment, the following issues were observed across datasets:

* Incorrect or inconsistent **data types** (dates, numbers stored as text)
* **Blank or null values** in key fields (Customer Name, Pump Status)
* **Duplicate records** across time periods
* Inconsistent **naming conventions** for customers and service personnel
* Date format mismatches impacting time intelligence

---

## 4. Preprocessing Steps Performed

### 4.1 Data Type Standardization

* Converted date fields to **Date** data type
* Ensured numeric fields (Value, Potential) were set to **Decimal / Whole Number**
* Validated text fields for categorical consistency

**Outcome:** Prevented calculation errors and ensured reliable aggregations.

---

### 4.2 Column Renaming & Standardization

* Renamed technical column headers to **business-friendly names**
* Standardized naming across OB Data, IB Data, and mapping tables

**Outcome:** Improved readability and reduced ambiguity during modeling.

---

### 4.3 Handling Missing & Blank Values

* Replaced irrelevant blanks with **"Unknown"** where appropriate
* Retained critical blanks for business validation
* Filtered out records missing mandatory identifiers (e.g., Pump ID)

**Outcome:** Maintained analytical accuracy without hiding data quality issues.

---

### 4.4 Duplicate Record Handling

* Identified duplicates using key combinations (Customer, Pump ID, Year)
* Removed exact duplicates after validation

**Outcome:** Avoided double counting in KPIs and measures.

---

### 4.5 Date Normalization

* Created consistent **Year** and **Year-Month** fields
* Aligned source dates with the Calendar table

**Outcome:** Enabled accurate trend and time-based analysis.

---

### 4.6 Pump Status Normalization

* Standardized pump status values into:

  * Operational
  * Inactive
  * Lost

**Outcome:** Ensured consistent classification across visuals and measures.

---

## 5. Error Handling & Validation

* Reviewed Power Query error rows
* Corrected type conversion issues
* Logged unresolved anomalies for stakeholder review

---

## 6. Performance Optimizations

* Removed unused columns early in Power Query
* Disabled load for intermediate queries
* Applied filters as early as possible in transformations

---

## 7. Output of Preprocessing Phase

The output of this phase is a set of **clean, standardized, and validated tables** ready for data modeling and DAX calculations.

---

## 8. Dependencies

* Relies on accurate source data from business systems
* Feeds directly into **Data Modeling (05_Data_Modeling.md)**

---

*Next Document: `05_Data_Modeling.md`*

