# Interim Report: Solar Data Discovery - Week 0 (Senegal Focus)

**Project:** Solar Data Discovery: Cross-Country Solar Farm Analysis  
**Name:** Miheret Girmachew 
**Date:** May 20, 2025

---

## 1. Introduction – Project Overview and Understanding

This report details the progress made during **Week 0** of the **10 Academy "Solar Data Discovery" challenge**, specifically focusing on the initial analysis of solar farm data from **Senegal**.

The **primary business objective** is to support **MoonLight Energy Solutions** by analyzing environmental data to identify key trends and provide data-driven recommendations for high-potential regions for solar installation.

This interim submission covers:
- The setup of the development environment
- The approach and initial findings for the **Exploratory Data Analysis (EDA)** of the Senegal dataset

> I understand this week is designed to be intensive, focusing on foundational skills like version control, data handling, and exploratory analysis — all critical for data-driven decision-making in real-world scenarios.

---

## 2. Methodology – Process, Progress So Far, and Results

My approach adheres to the structured tasks of the challenge, emphasizing **systematic data exploration** and **robust version control**.

### A. Task 1: Git & Environment Setup ✅

This crucial first task ensures a **reproducible and collaborative** development environment.

#### Summary of Actions:

- **Repository Initialization:**
  - Created a new public GitHub repo: `solar-challenge-week1`
  - Cloned locally and set up Python virtual environment (`venv`)

- **Branching & Commits:**
  - Created `setup-task` branch
  - Sample commits:
    - `init: add .gitignore` (ignores `data/`, `*.csv`, `venv/`, etc.)
    - `chore: venv setup and requirements.txt` (pandas, numpy, matplotlib, etc.)
    - `ci: add GitHub Actions CI workflow`
    - `docs: add initial README with setup instructions`

- **CI/CD Setup:**
  - `.github/workflows/ci.yml` runs `pip install -r requirements.txt` and checks Python version on `push`/`pull_request`

- **README & Folder Structure:**
  - Documented:
    - Overview
    - Environment setup steps
    - Folder structure: `.github/`, `data/`, `notebooks/`, `src/`, `scripts/`, `tests/`

- **Merge Strategy:**
  - `setup-task` branch merged into `main` via Pull Request

#### ✅ Results & KPI:
- Fully functional and version-controlled development environment
- **KPI "Dev Environment Setup" met**

---

### B. Task 2: Data Profiling, Cleaning & EDA (Senegal) – _In Progress_

#### Branch & Notebook:
- Created branch `eda-senegal`
- Notebook: `notebooks/senegal_eda.ipynb`

#### Approach & Outline:

##### ✅ Data Loading and Initial Inspection:
- File: `senegal_solar_data.csv` (semicolon-delimited)
- Used: `delimiter=';'` in `pd.read_csv()`
- Data overview:
  - Shape: 561,600 rows × 13 columns
  - Converted time column to `datetime64[ns]`
  - `DtypeWarning` for `comments` column noted

##### ✅ Summary Stats & Missing Values:
- Used: `df.describe().T`, `df.isnull().sum()`
- Notable:
  - `comments`: 99.56% missing
  - `relative_humidity`: 0.41% missing
  - `dhi_rsi`: 0.028% missing

##### ✅ Outlier Detection & Cleaning:
- Clipped negative `ghi_sil` values to 0
- Used Z-scores to detect outliers in key columns (flagged ~4437 rows)
- Imputed missing:
  - `dhi_rsi` and `relative_humidity` with median
  - `comments` with "No Comment"
- Saved clean file to `data/senegal_clean.csv` (gitignored)

##### 🔄 Time Series Analysis (In Progress):
- **Goal:** Identify seasonal/diurnal patterns
- Planned visualizations:
  - Line plots: `ghi_sil`, `ghi_pyr`, etc.
  - Aggregated daily/monthly/hourly trends

##### 🔄 Cleaning Impact Analysis (Planned):
- Compare irradiance values before/after `sensor_cleaning == 1`

##### 🔄 Correlation Analysis (Planned):
- Heatmap: correlations among key variables
- Scatter plots: e.g., `wind_speed` vs. `ghi_sil`

##### 🔄 Wind & Distribution Analysis (Planned):
- Wind rose (via `windrose`)
- Histograms with KDE for irradiance, temperature, etc.

##### 🔄 Temperature Analysis (Planned):
- Focus: `relative_humidity` vs. `air_temperature` and `ghi_sil`

##### 🔄 Bubble Chart (Planned):
- Plot: `ghi_sil` vs. `air_temperature`, bubble = `relative_humidity`

#### ✅ KPIs Addressed:
- Applied EDA techniques
- Demonstrated statistical understanding with Z-scores, summaries

---

## 3. Challenges & Solutions

### ✅ Encountered:
- **CSV delimiter issue:** Used `delimiter=';'`
- **Negative values in `ghi_sil`:** Clipped to 0
- **DtypeWarning for `comments`:** Not critical — safely ignored

### 🔄 Anticipated:
- **Interpreting complex plots (e.g., wind rose):**
  - Solution: Focus on clarity and physical interpretation
- **Performance issues with large dataset:**
  - Solution: Use sampling and aggregation for plots
- **Data quality differences in Benin/Togo:**
  - Solution: Use flexible, reusable EDA template per country

---

## 4. Future Plan (Week 0 Remaining)

### 🔜 Complete Senegal EDA
- Wrap up remaining plots in `senegal_eda.ipynb`
- Commit changes to `eda-senegal`, merge via PR

### 🔜 Repeat Task 2 for Benin & Togo
- Create `eda-benin` and `eda-togo` branches
- Clean data & export `benin_clean.csv`, `togo_clean.csv`

### 🔜 Task 3: Cross-Country Comparison
- Branch: `compare-countries`
- File: `compare_countries.ipynb`
- Load all cleaned CSVs
- Perform:
  - Boxplots
  - Summary tables
  - ANOVA/Kruskal-Wallis tests
- Document key insights

### ⚡ Bonus (If Time Allows)
- Try a basic **Streamlit dashboard** on `dashboard-dev` branch

### ✅ Final Report & Submission (by May 22, 2025 – 8:00 PM UTC)
- Medium-style blog or PDF
- Ensure:
  - Clean GitHub repo
  - All code on `main`
  - Screenshots if dashboard created

---

## 5. Conclusion – Summary and Confidence

- **✅ Git & CI/CD setup complete**
- **✅ Senegal dataset cleaned and profiled**
- Initial insights highlight trends and quality issues
- Clear roadmap to complete Benin, Togo, and comparison steps
- Confident in timely delivery and ability to extract actionable insights for MoonLight Energy Solutions

---
