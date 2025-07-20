# 💼 AMD Inc. Quarterly Financial Dashboard (2020–2024)

This project presents a detailed financial analysis dashboard for **Advanced Micro Devices (AMD) Inc.**, covering quarterly data from **Q1 2020 to Q2 2024**. The dashboard enables insights into AMD’s revenue, profitability, segment performance, and financial health through interactive Power BI visualizations, backed by Python-based data extraction from original financial PDFs.

![AMD Dashboard Preview](https://github.com/mkaran02/AMD-Inc-Financial-Dashboard/blob/main/Financial_Analysis_Of_AMD.inc.png?raw=true)


---

## 🎯 Project Objective

To extract, clean, analyze, and visualize AMD Inc.’s quarterly financial reports to:
- Track company growth and financial health over 5 years
- Identify high-performing business segments
- Highlight trends in Revenue, Net Income, EBITDA, and more
- Build a compelling dashboard for business intelligence and resume showcase

---

## 🛠️ Tools & Technologies Used

| Category              | Tools & Libraries                                   |
|-----------------------|-----------------------------------------------------|
| PDF Data Extraction   | `pdfplumber`, `PyMuPDF (fitz)`                      |
| Data Cleaning         | `Python`, `Pandas`, `NumPy`                         |
| Visualization         | `Power BI Desktop`                                  |
| File Formats          | `.pdf`, `.xlsx`,                   |
| Dashboard Hosting     | GitHub, Power BI Screenshot (for portfolio)         |

---

## 📂 Project Structure
📁 AMD-Financial-Dashboard/
│
├── 📄 README.md
├── 📊 amd.ipynb # Python code to extract and clean PDF data
├── 📂 pdfs/ # 20 quarterly financial reports from AMD
├── 📄 master_financials.xlsx # Cleaned master financial metrics
├── 📄 segment_performance.xlsx # Cleaned segment-level revenue & income
├── 📄 AMD_Dashboard.pbix # Final Power BI report
├── 📸 amd_dashboard.png # Dashboard preview image



---

## 📥 Data Sources

- Official AMD Quarterly Financial Reports (2020–2024) from:  
  🔗 [AMD Investor Relations](https://www.amd.com/en/investors/financial-information)

---

## 🧠 Key Performance Indicators (KPIs)

| KPI                         | Description                                         |
|-----------------------------|-----------------------------------------------------|
| **Total Revenue**           | Total company revenue per quarter/year              |
| **Net Income**              | Profits after all expenses                          |
| **Gross Margin %**          | Efficiency of revenue after production costs        |
| **Free Cash Flow (FCF)**    | Cash available after operating & capital expenses   |
| **Adjusted EBITDA**         | Earnings before interest, taxes, depreciation, etc. |
| **EPS (Earnings per Share)**| Per-share profit available to shareholders          |
| **YoY Revenue Growth %**    | Year-over-Year revenue comparison                   |
| **QoQ Revenue Growth %**    | Quarter-over-Quarter revenue comparison             |

---

## 📈 Dashboard Visuals & Insights

| Visual Type                    | Description & Purpose                                                                 |
|-------------------------------|----------------------------------------------------------------------------------------|
| **KPI Cards**                 | Display total Revenue, Net Income, Avg FCF, Avg EBITDA, Avg Gross Margin %             |
| **Line Chart**                | Trends of Revenue & Net Income (yearly comparison)                                     |
| **Bar Chart**                 | Compare FCF, Total Cost of Sales, and EBITDA by year                                   |
| **Pie Chart**                 | Total Assets split into Equity and Liabilities                                         |
| **Matrix Table**             | Compare QoQ Growth, YoY Growth, and Gross Margin across quarters                        |
| **Segment-wise Bar Chart**    | Revenue and Operating Income across all segments by year                               |
| **Slicers**                  | Dynamic filters for Quarter, Year, and Segment Name                                     |

---

## 🔁 Workflow Breakdown

### ✅ Phase 1: Understand the Data
- Explored AMD’s quarterly PDFs
- Identified required values:
  - Income Statement: Revenue, Gross Margin, Net Income, EPS
  - Balance Sheet: Total Assets, Liabilities, Equity
  - Cash Flow: Free Cash Flow
  - Segment Data: Segment-wise Revenue & Operating Income

---

### ✅ Phase 2: Extract & Clean Data (Python)

**Key Steps in `amd.ipynb`:**
- Parsed 20+ PDFs using `pdfplumber` and some manual changed and addings required because inaccuracy of pdfplumber
- Extracted financial tables from different formats
- Handled:
  - Missing values
  - Segment name changes across years
- Calculated:
  - `Gross Margin % = (Gross Margin / Revenue) × 100`
  - YoY and QoQ growth using `pandas shift()`

**Output Files:**
| File Name                  | Description                                  |
|---------------------------|----------------------------------------------|
| `master_financials.xlsx`  | Cleaned KPIs (1 row per quarter)             |
| `segment_performance.xlsx`| Segment revenue & income (multiple rows per quarter) |

---

### ✅ Phase 3: Data Transformation in Power BI

- Imported Excel files into Power BI
- Used **Power Query Editor** to:
  - Combine `Year` + `Quarter` → `Period`
  - Replace blanks with nulls or 0
  - Ensure correct data types
- Created DAX Measures for:
  - Average Operating Income by Segment
  - Revenue growth percentages
  - KPI aggregations

---

### ✅ Phase 4: Power BI Visualization

- Applied attractive dark purple theme
- Added AMD logo, custom background
- Made dashboard dynamic using:
  - `Slicers` for Quarter & Segment
  - `DAX Measures` for custom KPIs
- Used card visuals, charts, and matrix table

---

## 📊 Sample DAX Measures

```dax
-- Average Operating Income (Computing & Graphics)
Avg_OperatingIncome_CG =
CALCULATE(
    AVERAGE(segment_performance[Segment Operating Income ($M)]),
    segment_performance[Segment Name] = "Computing & Graphics"
)

-- Gross Margin Percentage
Gross_Margin_Percent =
DIVIDE(master_financials[Gross Margin ($M)], master_financials[Revenue ($M)]) * 100


