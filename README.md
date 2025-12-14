<div align="center">

# 🌍 Global Economic & Demographic Trends Analysis  
### *A Power BI Portfolio Project (1960–2017)*

<img src=https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExbXY2MmNha3Z0dmY4am1vbXlmdTcweGdrbTVmZGx1N3JlcHBlajF0dCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/bsbWrS0aqbS0w/giphy.gif>

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Data Analysis](https://img.shields.io/badge/Data_Analysis-0078D4?style=for-the-badge&logo=xbox&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

<br>

> **"Data is the new oil. It’s valuable, but if unrefined it cannot really be used."**  
> *– Clive Humby*

</div>

---

## 📽️ 1. Project Overview

We analyze nearly **60 years of global data** (1960–2017) to visualize how our world has changed. This project uses **Power BI** to transform raw World Development Indicators into interactive stories about population growth, economic shifts, and social progress.

<div align="center">
  <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbXN1OTNic2Y2cXFuNGkxd2l2ejF1MTNmeW14a2d4bGVlM3lxY2owaCZlcD12MV9naWZzX3NlYXJjaCZjdD1n/lOfpvYQoiJW03vpJhP/giphy.gif">
  <br>
  <em>(Transforming raw numbers into visual insights)</em>
</div>

---

## 🎯 2. Objectives

<table border="0">
 <tr>
    <td width="300px">
      <img src="https://media.giphy.com/media/3o7TKSjRrfIPjeiVyM/giphy.gif" width="100%" alt="Checklist Animation">
    </td>
    <td>
      <h3>What we aim to achieve:</h3>
      <ul>
        <li>✅ <strong>Visualize trends</strong> in Population, GDP, and Literacy over 5 decades.</li>
        <li>✅ <strong>Analyze correlations</strong> between economic stability and social indicators.</li>
        <li>✅ <strong>Compare regions</strong> to highlight global inequalities.</li>
        <li>✅ <strong>Create interactive dashboards</strong> for deep-dive exploration.</li>
      </ul>
    </td>
 </tr>
</table>

---

## 📂 3. Data Sources

We utilized the **World Development Indicators** dataset, enriching it with metadata for regional analysis.

| 📅 Dataset Type | 🔍 Contents | 💾 Format |
| :--- | :--- | :--- |
| **Main Indicators** | Population, GDP, Literacy, Infant Mortality, Migration | CSV / Excel |
| **Metadata** | Region Classifications, Income Groups | Excel |
| **Database** | `CountriesWorld` Table (SQL) | SQL |

---

## 🧹 4. Data Cleaning & Transformation

Before visualization, the data underwent rigorous cleaning using **Power Query**.

<div align="center">
  <img src="https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExb2didjIxcGUwempueGl5Y2Z3emczNmlraGN3a2NoZTBhcXBoZjB2dSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/7jtU9sxHNLZuv8HZCa/giphy.gif">
</div>

<details>
<summary>🔻 <strong>Click to view detailed generic cleaning steps</strong></summary>
<br>

1.  **Removed Duplicates & Nulls:** Filtered out empty rows and duplicate entries to ensure data integrity.
2.  **Header Promotion:** Used first rows as headers and corrected data types (Text, Decimal Number, Whole Number).
3.  **Median Imputation:** Filled missing values (e.g., Literacy Rates) using regional medians to avoid skewing averages.
4.  **Unpivoting:** Converted "Year" columns (1960, 1961... 2017) into a single "Year" attribute for time-series analysis.
5.  **Appending:** Combined multiple GDP sheets (1960-1980, 1981-1999, 2000-2016) into one master table.
6.  **Modeling:** Established `One-to-Many` relationships between the `Metadata` (Region) and `Data` tables via `Country Code`.

</details>

---

## 🧮 5. DAX Measures

We used **DAX (Data Analysis Expressions)** to create dynamic calculations that respond to slicers and filters.

```dax
/* Example Measure: YoY Growth */
YoY GDP Growth % = 
VAR CurrentGDP = [Total GDP]
VAR PriorGDP = CALCULATE([Total GDP], SAMEPERIODLASTYEAR('Date'[Date]))
RETURN
DIVIDE(CurrentGDP - PriorGDP, PriorGDP, 0)
```

**Key Measures Included:**
*   `GDP Per Capita`
*   `Pop Density Change %`
*   `Infant Mortality Reduction Rate`
*   `% of World Population`

---

## 📊 6. Dashboard Showcase

<div align="center">

### 🌍 Dashboard 1: Global Overview
*A high-level view of the planet's economic health.*

<img width="1350" height="748" alt="image" src="https://github.com/user-attachments/assets/6d2017cc-282a-4248-be7b-cc443524562b" />


<br>

### 🏳️ Dashboard 2: Country Analysis
*Drill down into specific nations' performance.*

<img width="1352" height="758" alt="image" src="https://github.com/user-attachments/assets/4ed65b9d-af1e-481d-a9d0-b8f88b755bab" />


</div>

---

## 💡 7. Insights & Findings

<table border="0">
 <tr>
    <td width="200px">
      <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExdjY1emZjYXpwOTd0dGZsdDBzNXV2aW5wMmFnZDN6bHA5dHAxN2xnaSZlcD12MV9naWZzX3NlYXJjaCZjdD1n/L4RZloecys3VCAojKs/giphy.gif">
    </td>
    <td>
      <ul>
        <li><strong>Population Explosion:</strong> Global population has surged, but growth rates are slowing in developed nations.</li>
        <li><strong>The Wealth Gap:</strong> A small percentage of High-Income countries control the majority of global GDP.</li>
        <li><strong>Health & Wealth:</strong> There is an undeniable correlation (R² > 0.8) between <em>Internet Usage/Literacy</em> and <em>GDP Per Capita</em>.</li>
        <li><strong>Migration:</strong> Net migration is overwhelmingly positive towards high-income regions, draining talent from developing areas.</li>
      </ul>
    </td>
 </tr>
</table>

---

## 🛠️ 8. Tools & Tech Stack

<div align="center">
  <br>
  <img src="https://img.shields.io/badge/Microsoft%20Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white" />
  <img src="https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=Power%20BI&logoColor=white" />
  <img src="https://img.shields.io/badge/DAX-0078D4?style=for-the-badge&logo=microsoft&logoColor=white" />
  <img src="https://img.shields.io/badge/Power%20Query-F2C811?style=for-the-badge&logo=power-bi&logoColor=white" />
  <br><br>
  <img src="https://media.giphy.com/media/du3J3cXyzhj75IOgvA/giphy.gif" width="100" alt="Gears turning">
</div>

---


## 👋 10. Contact

### Let's Connect!

[<img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" />](https://linkedin.com/in/Vishxnu)
[<img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white" />](https://github.com/vishxnu)
[<img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white" />](mailto:vishnuskillx@gmail.com)

</div>
