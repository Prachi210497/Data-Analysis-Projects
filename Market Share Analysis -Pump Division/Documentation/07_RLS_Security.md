Implementing Row-Level Security (RLS) was to ensure controlled data access so that users can view only the data relevant to their assigned **service person(Sales), region, or hierarchy**.

This approach supports data confidentiality, compliance, and role-based reporting within the Power BI solution.

### RLS Design Approach

Row-Level Security was implemented using a dedicated RLS table in combination with a SAM_Bridge table, allowing flexible and scalable access control.

This design avoids hardcoding user access in fact tables and ensures centralized security management.

---

### RLS Tables Overview

**RLS Table**

It Contains the list of authorized users and their assigned service scope.

**Key Columns:**

User Email / User ID

Service Person

Role / Access Level

---

## SAM_Bridge Table

Acts as an intermediary between transactional data and the RLS table.
 
Key Columns:

Service Person (Sales)

---

### Relationship Strategy

SAM_Bridge → RLS relationship is active

IB_Data / OB_Data → RLS relationships are kept inactive

Security flows through SAM_Bridge, ensuring consistent access across datasets

This design prevents ambiguity and maintains performance.

---

### RLS Role Configuration

Sample RLS Filter
[RLS].[User Email] = USERPRINCIPALNAME()

This ensures that each user sees only the data mapped to their identity.

---

### Security Validation

RLS was validated by:

Testing with multiple user accounts

Verifying cross-filter behavior across IB and OB reports

Ensuring no data leakage across service hierarchies

---

### Business Benefits

Protects sensitive business data

Ensures users access only authorized information

Supports secure sharing of dashboards across teams

Aligns with enterprise data governance standards

---

### Outcome

The RLS implementation provided a **secure, scalable, and maintainable access control mechanism**, enabling confident dashboard sharing across multiple roles and hierarchies.

