# Power-BI-Finance-Analysis-Dashboard
I’m excited to share my latest Power BI Finance Analysis project, where I transformed transaction data into an interactive dashboard to generate meaningful financial insights.

overview-analysis-Dashboard
<img width="960" height="511" alt="finance_img" src="https://github.com/user-attachments/assets/4914492d-ad26-4058-b351-f773f0d9969f" />

transaction
<img width="960" height="510" alt="finance_img2" src="https://github.com/user-attachments/assets/22d68037-4fef-490c-97d1-214fdfd3d397" />


## DAX Measures – Financial Analysis Dashboard

The following DAX measures were developed in Power BI to calculate key financial KPIs, analyze transaction performance, and compare financial metrics across different years.

### 1. Total Amount

Calculates the total amount of all financial transactions.

```dax
Total Amount =
SUM(finance_transactions[amount])
```

### 2. Total Transactions

Calculates the total number of unique transactions.

```dax
Total Transaction =
DISTINCTCOUNT(finance_transactions[transaction_id])
```

### 3. Average Transaction Value

Calculates the average value of financial transactions.

```dax
Avg Transaction value =
AVERAGE(finance_transactions[amount])
```

### 4. Total Fee

Calculates the total fees collected from financial transactions.

```dax
Total fee =
SUM(finance_transactions[fee_amount])
```

### 5. Total Tax

Calculates the total tax collected from financial transactions.

```dax
Total tax =
SUM(finance_transactions[tax_amount])
```

### 6. Dynamic Measure Selection

Created a Field Parameter to allow users to dynamically switch between different financial KPIs in the dashboard.

```dax
Dynamic Measure = {
    ("Total Amount", NAMEOF([Total Amount]), 0),
    ("Total Transaction", NAMEOF([Total Transaction]), 1),
    ("Total tax", NAMEOF([Total tax]), 2),
    ("Total fee", NAMEOF([Total fee]), 3)
}
```

### 7. Year-over-Year (YoY) Analysis

Year-over-Year analysis was performed to compare current-year performance with the previous year.

**Previous Year Amount**

```dax
Previous-year-Amount =
CALCULATE(
    [Total Amount],
    SAMEPERIODLASTYEAR('Date'[Date])
)
```

**YoY Amount**

```dax
YOY =
[Total Amount] - [Previous-year-Amount]
```

**Previous Year Transaction**

```dax
Previous-year-Transaction =
CALCULATE(
    [Total Transaction],
    SAMEPERIODLASTYEAR('Date'[Date])
)
```

**YoY Transaction**

```dax
YoY Transaction =
[Total Transaction] - [Previous-year-Transaction]
```

**Previous Year Average Transaction**

```dax
Previous-year-avg Transaction =
CALCULATE(
    [Avg Transaction value],
    SAMEPERIODLASTYEAR('Date'[Date])
)
```

**YoY Average Transaction**

```dax
YoY avg Transaction =
[Avg Transaction value] - [Previous-year-avg Transaction]
```

**Previous Year Fee**

```dax
Previous-year-Fee =
CALCULATE(
    [Total fee],
    SAMEPERIODLASTYEAR('Date'[Date])
)
```

**YoY Fee**

```dax
YOY Fee =
[Total fee] - [Previous-year-Fee]
```

**Previous Year Tax**

```dax
Previous-year-tax =
CALCULATE(
    [Total tax],
    SAMEPERIODLASTYEAR('Date'[Date])
)
```

**YoY Tax**

```dax
YOY Tax =
[Total tax] - [Previous-year-tax]
```

---

### DAX Analysis Summary

| Measure Category | Business Purpose |
|---|---|
| Total Amount | Measures overall transaction value |
| Total Transactions | Tracks transaction volume |
| Average Transaction Value | Measures average transaction size |
| Total Fee | Analyzes fee revenue |
| Total Tax | Tracks tax collection |
| Dynamic Measure | Enables interactive KPI selection |
| YoY Analysis | Compares current and previous-year performance |

**Key DAX Functions Used:**

- `SUM()` – Calculates total financial values.
- `DISTINCTCOUNT()` – Counts unique transactions.
- `AVERAGE()` – Calculates average transaction value.
- `CALCULATE()` – Modifies filter context for calculations.
- `SAMEPERIODLASTYEAR()` – Retrieves values for the corresponding previous-year period.
- `NAMEOF()` – References measures in Field Parameters.


YOY Fee = [Total fee]- [Previous-year-Fee]

11.Year on Year of tax
YOY Tax = [Total tax]- [Previous-year-tax]
