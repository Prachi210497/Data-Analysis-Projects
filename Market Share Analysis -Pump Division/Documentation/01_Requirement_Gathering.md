# 01. Requirement Gathering

## 1. Purpose of This Document

This document captures the **business requirements, objectives, stakeholders, and key questions** for the **Market Share Analysis Report**. It serves as the foundation for all downstream activities including data modeling, DAX development, visualization, and validation.

---

## 2. Business Context

The Pump Business operates across multiple customers, regions, and service personnel. Data related to **sales (Order Booking)**, **installed base**, and **service ownership** exists in silos, making it difficult for stakeholders to:

* Track true market share over time
* Identify operational vs inactive pumps
* Understand revenue potential and losses
* Align sales and service actions

The absence of a unified analytical view resulted in **manual analysis, inconsistent numbers, inaccurate data and delayed decisions**.

---

## 3. Business Objectives

The primary objectives of this project are:

* Provide a **single source of truth** for market share reporting
* Enable **year-wise and customer-wise market share analysis**
* Track **operational, inactive, lost pumps and Stand By pumps**
* Identify **high-potential customers and at-risk accounts**
* Support **sales prioritization and service planning**

---

## 4. Stakeholders

| Stakeholder              | Role                                  | Key Expectations                                     |
| ------------------------ | ------------------------------------- | ---------------------------------------------------- |
| Sales Team               | Revenue growth & customer acquisition | Market share, customer potential, lost opportunities |
| Service Team             | Pump lifecycle & uptime               | Operational vs inactive pumps, service ownership     |
| Area / Regional Managers | Performance monitoring                | Region-wise trends, team performance                 |
| Business Leadership      | Strategic decisions                   | High-level KPIs, trends, risks                       |

---

## 5. In-Scope Requirements

### Analytical Scope

* Market share calculation by year
* Customer-wise and service-person-wise analysis
* Pump status classification (Operational / Inactive / Lost / Stand By)
* Revenue and potential value analysis

### Functional Scope

* Interactive filters (Year, Customer, Service Person, State)
* Drill-down from summary to customer-level details
* Secure access based on user role

---

## 6. Out-of-Scope (Phase 1)

* Product-level / segment-level analysis
* Mobile-optimized dashboards
* Predictive or forecasting models
* Real-time data integration

(Planned for Phase 2)

---

## 7. Key Business Questions

* What is the **market share trend year-over-year**?
* Which customers contribute the **highest and lowest market share**?
* Where are **pumps becoming inactive or lost**?
* What is the **revenue impact of inactive pumps**?
* How does service ownership influence pump performance?

---

## 8. Assumptions

* Source data provided is system-generated and approved
* Pump status values are standardized across datasets
* Calendar year is the primary time dimension
* One pump is associated with one customer at a time

---

## 9. Risks & Mitigations

| Risk                       | Impact             | Mitigation                      |
| -------------------------- | ------------------ | ------------------------------- |
| Data quality issues        | Incorrect KPIs     | Data validation & preprocessing |
| Many-to-many relationships | Wrong aggregations | Bridge tables & model design    |
| Misinterpretation of KPIs  | Wrong decisions    | Clear definitions & training    |

---

## 10. Success Criteria

The project will be considered successful if:

* Stakeholders rely on the report for decision-making
* KPIs reconcile with source systems
* Filters and RLS behave as expected
* Manual reporting effort is reduced

---

## 11. Sign-off (Indicative)

Business stakeholders reviewed and agreed on the scope, objectives, and success criteria outlined in this document.


