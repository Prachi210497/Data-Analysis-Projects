# 06. DAX Measures

### Objective

The objective of this section is to document the key **DAX measures** created to support **market share analysis**, **performance tracking, and trend comparison** across **Installed Base (IB)** and **Order Booking (OB)** datasets.

All measures were designed to work seamlessly with:

**Calendar-based time intelligence**

**Service person hierarchy**

**Row-Level Security (RLS)**

---

### Base Measure
Base measures were created first to ensure **reusability**, **consistency**, and **performance optimization**

**1. Total potential**

Total Pump Potential = 
VAR Result = 
    [TP Active Pumps Selected Year] + [TP (Inactive Pumps Selected Year)] + [TP (Lost Pumps Selected Year)] + [TP (Standby Pumps Selected Year)]
RETURN
    IF(ISBLANK(Result), 0, Result)

**2. Active Potential**
   
TP Active Pumps Selected Year = 
VAR Result =
    CALCULATE(
        SUM('IB - Data'[Total Potential]),
        'IB - Data'[Pump Status] = "Operational",
        KEEPFILTERS('Calendar'[Date].[Year])
    )
RETURN
    IF(ISBLANK(Result), 0, Result)

**3. Inactive Potentail** 

TP (Inactive Pumps Selected Year) = 
VAR Result =
    CALCULATE(
        SUM('IB - Data'[Total Potential]),
        'IB - Data'[Pump Status] = "Inactive",
        KEEPFILTERS('Calendar'[Date].[Year])
    )
RETURN
    IF(ISBLANK(Result), 0, Result)

**4. Standby Potential**

TP (Standby Pumps Selected Year) = 
VAR Result =
    CALCULATE(
        SUM('IB - Data'[Total Potential]),
        'IB - Data'[Pump Status] = "Stand By",
        KEEPFILTERS('Calendar'[Date].[Year])
    )
RETURN
    IF(ISBLANK(Result), 0, Result)

**5. Lost Potential**

TP (Lost Pumps Selected Year) = 
VAR Result =
    CALCULATE(
        SUM('IB - Data'[Total Potential]),
        'IB - Data'[Pump Status] = "Lost",
        KEEPFILTERS('Calendar'[Date].[Year])
    )
RETURN
    IF(ISBLANK(Result), 0, Result)

**6. Total Pumps**

Total Pumps = SUM('IB - Data'[Qty])

**7. Active Pumps**

Operational Pumps = 
CALCULATE(
    SUM('IB - Data'[Qty]),
    'IB - Data'[Pump Status] = "Operational"
)

**8. Inactive Pumps**

Inactive Pumps = 
CALCULATE(
    SUM('IB - Data'[Qty]),
    'IB - Data'[Pump Status] = "Inactive"
)

**9. Standby Pumps**

Standby Pumps = 
CALCULATE(
    SUM('IB - Data'[Qty]),
    'IB - Data'[Pump Status] = "Stand By"
)

**10. Lost Pumps**

Lost Pumps = 
CALCULATE(
    SUM('IB - Data'[Qty]),
    'IB - Data'[Pump Status] = "Lost"
)

**11. Cumulative Potential (for Active Pumps)**

Cumulative Potential Value (Operational) = 
CALCULATE(
    [Total Potential Value],
    FILTER(
        ALLSELECTED('Calendar'[Date].[Year]),
        'Calendar'[Date].[Year] <= MAX('Calendar'[Date].[Year])
    ),
    'IB - Data'[Pump Status] = "Operational"
)

**12. Total potential For Active Pumps** 

TP Active Pumps Selected Year = 
VAR Result =
    CALCULATE(
        SUM('IB - Data'[Total Potential]),
        'IB - Data'[Pump Status] = "Operational",
        KEEPFILTERS('Calendar'[Date].[Year])
    )
RETURN
    IF(ISBLANK(Result), 0, Result)

**13. Market Share %**

Market_Share (%) = 
VAR CurrYear = MAX( 'Calendar'[Year] )

VAR OrderValue_Year =
    CALCULATE(
        SUM( 'OB_Data'[Total Value -INR] ),
        FILTER( ALL( 'Calendar' ), 'Calendar'[Year] = CurrYear )
    )

VAR CumPotential_UpToYear =
    CALCULATE(
        SUM( 'IB - Data'[Total Potential] ),
        'IB - Data'[Pump Status] = "Operational",
        FILTER( ALL( 'Calendar' ), 'Calendar'[Year] <= CurrYear )
    )

RETURN
DIVIDE( OrderValue_Year, CumPotential_UpToYear, 0 )

**14. Cummulative potential without Slicer for Active Pumps**

CPV (Operational) = 
CALCULATE(
    [Total Potential Value],
    FILTER(
        ALL('Calendar'[Date]),   // ignore slicer on Calendar completely
        'Calendar'[Date] <= MAX('Calendar'[Date])
    ),
    'IB - Data'[Pump Status] = "Operational"
)

**15. Quantity of New Pumps Added each year** 

New Pumps (Qty) = 
CALCULATE(
    SUM('IB - Data'[Qty]),
    FILTER(
        'IB - Data',
        NOT(ISBLANK('IB - Data'[Qty]))
    )
)

**16. Quantity of Operational Pumps**

QTY Of Operational Pumps = 
CALCULATE(
    SUM('IB - Data'[Qty]),
    'IB - Data'[Pump Status] = "Operational"
)

**17. Operational Pump potentail** 

Operationa Pump Potential = CALCULATE(
    SUM('IB - Data'[Total Potential]),
    'IB - Data'[Pump Status] = "Operational"
)

---

### Result

The implemented DAX measures enabled:

* Accurate market share and growth calculations
* Consistent results across IB and OB datasets
* Secure reporting with RLS enforcement
* Scalable and maintainable measure logic

These measures formed the analytical backbone of the dashboards and provides accurate results.
