# 💰 Financial-Analysis-Dashboard--Power-BI--EN

> Financial analysis of a company’s income and expenditure over 2019, 2020 and 2022, focusing on profit margins and trends by component.

---

## 📌 Table of Contents

- About the Project
- Objectives of the Analysis
- Tools Used
- Dataset Structure
- Data Processing
- Dashboard
- DAX Measures
- Key Findings
- Recommendations
- How to View

---

## 📁 About the Project

This project involves a financial analysis based on monthly data for a company’s **revenue and expenses**, covering the years **2019, 2020 and 2022**; there is no data for 2021, and unfortunately I have not been able to find out why.

The main objective is to understand the company’s financial performance, identify the components with the greatest impact on revenue and expenditure, and track the profit margin over time.

---

## 🎯 Objectives of the Analysis

- Track the overall evolution of revenue and expenses by year
- Identify the revenue and expense components with the greatest weight
- Calculate and monitor the profit margin
- Compare financial performance across the three available years

---

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| **Power BI Desktop** | Building the dashboard and visualisations |
| **DAX** | Creating calculated measures |
| **Excel (.xlsx)** | Source of financial data |

---

## 📂 Dataset Structure

The `DadosFinanceiros.xlsx` file contains monthly data organised as follows:

| Column | Description |
|---|---|
| `Tipo` | Revenue or Expense |
| `Componente` | Specific category (e.g. Sales, Salaries) |
| `Jan-Dez 2019` | Monthly figures for 2019 |
| `Jan-Dec 2020` | Monthly figures for 2020 |
| `Jan-Dec 2022` | Monthly figures for 2022 |

### Revenue Components

| Component | Total (3 years) |
|---|---|
| Sales | €1,359,336.00 |
| Licensing | €232,200.00 |
| Rent | €119,175.00 |
| Advertising | €78,978.00 |
| Investments | €68,800.00 |
| Franchises | €61,600.00 |
| **Total Revenue** | **€1,920,089.00** |

### Expenditure Components

| Component | Total (3 years) |
|---|---|
| Administration | €462,000.00 |
| Technology | €277,000.00 |
| Salaries | €241,000.00 |
| Taxes | €70,000.00 |
| Security | €51,600.00 |
| Marketing | €51,317.00 |
| **Total Expenditure** | **€1,152,917.00** |

---

## 📂 Data Processing

Before taking the measurements and analysing the data, I needed to process it in Power BI. To do this, I had to access Power Query, and the data appeared as follows:

![Dashboard Preview](https://github.com/diogovent/Financial-Analysis-Dashboard--Power-BI--EN/blob/main/1.png)

To resolve this issue, I first needed to convert the first row into column names and change the column type (in some cases) from text to decimal:

![Dashboard Preview](https://github.com/diogovent/Financial-Analysis-Dashboard--Power-BI--EN/blob/main/2.png)

Finally, I needed to create a ‘Data’ column and a ‘Valor’ column; the latter was the only one for which I had to write my own code, as there was no quick way to solve the problem:

```dax
    = Table.UnpivotOtherColumns(#"Tipo Alterado1", {"Tipo", "Componente"}, "Data", "Valor")
```

After that, I simply converted the ‘Datas’ column, which was formatted as text, to a date type:

![Dashboard Preview](https://github.com/diogovent/Financial-Analysis-Dashboard--Power-BI--EN/blob/main/3.png)

---

## 📊 Dashboard

![Dashboard Preview](https://github.com/diogovent/Financial-Analysis-Dashboard--Power-BI--EN/blob/main/Dashboard.png)

The dashboard displays the following visuals:

**Top KPIs:**
- **Total Revenue:** €1.92 million
- **Total Expenses:** €1.15 million
- **Profit Margin:** 39.96%

**Visuals included:**
- **Top Segments (AI)** — Automatic segmentation by average value, identifying 7 distinct segments
- **Total Revenue by Component** — Horizontal bar chart showing that the main component of revenue is “Sales” at approximately €1,359 million (70.8%)
- **Total Expenses by Component** — Line/area chart with an average expense line (€192,152.83), showing that the main expense component
is ‘Administrative’, accounting for approximately 40.1%
- **Summary Table by Year** — Comparison of revenue and expenses by component in 2019, 2020 and 2022; there is no data for 2021, as
the ‘Matrix’ chart type was used; the totals at the bottom of the chart represent the total turnover and not the profit the company made

---

## 🧮 DAX measures

Total Revenue:
```dax
Total de Receitas = CALCULATE(SUM(DadosFinanceiros[Valor]),DadosFinanceiros[Tipo]="Receitas")
```

Total Expenses:
```dax
Total de Despesas = CALCULATE(SUM(DadosFinanceiros[Valor]),DadosFinanceiros[Tipo]="Despesas")
```

Profit Margin:
```dax
Margem de Lucro = DIVIDE([Lucro], [Total de Receitas], 0)
```

Total Profit:
```dax
Lucro = [Total de Receitas] - [Total de Despesas]
```

---

## 🔍 Key Findings

1. **Sales Dominate Revenue** — They account for over 70% of total revenue (€1.36m out of €1.92m)

2. **Profit Margin is Healthy** — 39.96% indicates that for every euro of revenue, almost 40 cents remains as profit

3. **Administrative Costs are the Largest Expense** — Accounting for 40% of total expenses (€462K out of €1.15M)

4. **Consistent Revenue Growth** — From 560K in 2019 to 755K in 2022, a growth of ~35%

5. **Expenses Have Also Increased** — From 287K in 2019 to 495K in 2022, so cost management is an area to monitor

6. **Sharp Rise in Salaries** — These rose from 40K in 2019 to 124K in 2022, reflecting the growth of the team

---

## 💡 Recommendations

1. **Control the Rise in Expenses**
    Expenses are rising faster than revenue, which is putting pressure on the margin, so I recommend:
       Implementing cost-control measures, particularly in key areas such as administration, to prevent a decline in profitability
   
2. **Monitor Profit Margin Over Time**
   The overall margin is good, but it is trending downwards, so I recommend:
       Establish regular monitoring of the profit margin (monthly or quarterly) to identify deviations and take timely action

3. **Reduce Reliance on Sales**
    Sales account for over 70% of revenue → concentration risk, so I recommend:
       Diversify revenue streams, strengthening areas such as licensing or investments to make the business more balanced

---

## 📌 How to view

1. Download the `.pbix` file available in this repository
2. Open it in **Power BI Desktop** (free)
3. The data file `DadosFinanceiros.xlsx` is included in the repository

4. Alternatively, you can access it via this link: https://app.powerbi.com/groups/me/reports/f1b1659c-e50e-4b8c-88be-ebcefc530607?pbi_source=desktop

---

## 👤 Author

Developed as a data analysis project for my personal portfolio.

[![LinkedIn](https://www.linkedin.com/in/diogo-ventura-4981bb254/)
[![GitHub](https://github.com/diogovent)














