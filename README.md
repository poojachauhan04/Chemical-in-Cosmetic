# Chemicals in Cosmetics Analysis 💄

An end-to-end data analytics project on 114K+ cosmetic product records from the California Safe Cosmetics Program, to find out which chemicals are reported most, which categories, companies, and brands report the most, and how reporting has changed over time, using Python.

---

## 📌 Project Overview

This project is framed as a consulting-style case study. The business scenario is fictional, but the data is real: the official public records of the California Safe Cosmetics Program (CSCP), run by the California Department of Public Health (CDPH).

A cosmetics regulator or beauty brand has a very large list of reported products and chemicals, but no single view of which chemicals, categories, companies, and brands matter most, or how reporting has changed over the years. The raw file also contains duplicate rows, missing values, and dates stored as plain text. This project cleans the raw data, builds new analysis columns, and answers business questions with Pandas and Seaborn.

**Result at a glance**

| Metric | Value |
|---|---|
| Raw Records | 114,635 |
| Cleaned Records | 114,381 (254 duplicate rows removed, 0.22%) |
| Unique Products | 33,716 |
| Unique Companies | 606 |
| Unique Brands | 2,713 |
| Unique Chemicals Reported | 123 |
| Most Reported Chemical | Titanium dioxide (93,479 records, about 82% of all records) |
| Largest Category | Makeup Products (non-permanent), about 66% of records |
| Top Reporting Company | L'Oreal USA (5,747 records) |
| Average Time Between Chemical Created and Updated | About 93 days |

---

## 🛠️ Tech Stack

- **Data Cleaning & Feature Engineering:** Python (Pandas, NumPy), Jupyter Notebook / Google Colab
- **Data Visualization:** Matplotlib, Seaborn
- **Analytical Concepts:** Univariate Analysis, Category Analysis, Company & Brand Analysis, Chemical Usage Analysis, Trend Analysis Over Time

---

## ❓ Business Problems Solved

1. **How big is the dataset?** Counted unique products, companies, brands, and chemicals.
2. **Which categories carry the most records?** Compared primary categories and subcategories.
3. **Which chemicals are used the most?** Ranked the top 10 most frequently reported chemicals.
4. **Which companies and brands report the most?** Ranked the top companies and brands by record count.
5. **How has reporting changed over time?** Checked records by year and when chemicals were removed.
6. **How often are chemical records updated?** Measured the time between a chemical record being created and updated.
7. **Which category has the most chemicals per product?** Compared average chemical count across categories.

**Who can use these insights:** regulators (which categories and chemicals to watch), brand and product teams (which chemicals appear in their category), and compliance teams (reporting patterns by company and year).

---

## 🗂️ Dataset Summary

**Source:** California Safe Cosmetics Program open data (CDPH).

| Detail | Value |
|---|---|
| File | `cscpopendata.csv` |
| Raw size | 114,635 rows × 22 columns |
| After cleaning | 114,381 rows × 16 columns |

| Column Group | Columns |
|---|---|
| Product | `CDPHId`, `ProductName`, `CSFId`, `CSF` |
| Company & Brand | `CompanyId`, `CompanyName`, `BrandName` |
| Category | `PrimaryCategoryId`, `PrimaryCategory`, `SubCategoryId`, `SubCategory` |
| Chemical | `CasId`, `CasNumber`, `ChemicalId`, `ChemicalName`, `ChemicalCount` |
| Dates | `InitialDateReported`, `MostRecentDateReported`, `DiscontinuedDate`, `ChemicalCreatedAt`, `ChemicalUpdatedAt`, `ChemicalDateRemoved` |

**How counts are defined:** one row is one product-and-chemical pair, so a product with two reported chemicals appears twice. "Records" means rows, and "unique products" means distinct product names.

---

## 🚀 Project Workflow

### Phase 1: Data Cleaning & Feature Engineering (Python)

| Audit finding (before cleaning) | Count | How it was handled |
|---|---|---|
| Duplicate rows | 254 | Removed |
| Missing `BrandName` | 227 | Filled with the most common brand (mode) |
| Missing `CasNumber` | 6,475 | Column dropped (not needed for analysis) |
| Missing `CSFId` / `CSF` | 33,731 / 34,156 | Columns dropped (not needed for analysis) |
| Date columns stored as text | 6 columns | Converted to datetime |

Other steps:

- Dropped columns not needed for analysis: `CSF`, `CSFId`, `CompanyId`, `PrimaryCategoryId`, `SubCategoryId`, `CasId`, `CasNumber`.
- Created new columns: `Discontinued_Month`, `MostRecentDateReported_year`, and chemical update lag (`ChemicalUpdatedAt` minus `ChemicalCreatedAt`).
- Final result: 114,381 records, which is 0.22% fewer than the raw 114,635. This is a cleaning result, not a business loss.

### Phase 2: Analysis & Visualization (Python)

- Univariate analysis of products, companies, brands, chemicals, and categories.
- Ranked top chemicals, companies, brands, categories, and subcategories using `value_counts()` and `groupby()`.
- Trend analysis of records by reporting year and chemical removals by year.
- Plotted results with Matplotlib and Seaborn.

---

## 💡 Key Insights

- The dataset covers **33,716 products**, **606 companies**, **2,713 brands**, and **123 chemicals**.
- **Titanium dioxide** is by far the most reported chemical, with 93,479 records. The next most reported, crystalline silica, has only 2,816.
- **Makeup Products (non-permanent)** is the largest category with 75,822 records, followed by **Nail Products** (15,347), **Skin Care Products** (7,680), and **Sun-Related Products** (4,939).
- The top subcategories are **Lip Color** (16,553), **Eye Shadow** (15,744), **Foundations and Bases** (14,095), **Nail Polish and Enamel** (9,945), and **Lip Gloss/Shine** (8,972).
- **L'Oreal USA**, **S+**, and **Coty** are the top reporting companies. **Sephora**, **NYX**, and **bareMinerals** are the top reporting brands.
- **Tattoos and Permanent Makeup** has the highest average number of chemicals per product record (about 1.48).
- Records by most recent reporting year peak in **2010** (21,362), with other high years in **2018** (12,775) and **2013** (12,429).
- Chemical records are updated about **93 days** after they are created, on average.

---

## ✅ Recommendations

➢ **Focus on Makeup and Nail Products** → These two categories hold about 80% of all records, so monitoring effort here covers most of the dataset.

➢ **Track Titanium Dioxide Closely** → It appears in the vast majority of records, so any rule change on it would affect most reported products.

➢ **Review Tattoo and Permanent Makeup Products** → They carry the most chemicals per product on average, even though they are a small category.

➢ **Encourage Consistent Reporting** → Reporting volume jumps sharply in some years (2010, 2013, 2018), so a regular reporting schedule would make year-over-year trends easier to compare.

➢ **Standardize Brand Names** → The same brand appears in different spellings (for example `Sephora` and `SEPHORA`), which splits counts. Cleaning brand names would make brand rankings more accurate.

---

## ⚠️ Limitations

- A record shows that a chemical was **reported** in a product. It does not show how much of the chemical is in the product, or that the product is unsafe.
- One product can have several rows (one per chemical), so row counts are not product counts.
- Missing `BrandName` values were filled with the most common brand, which can slightly overstate that brand's count.
- Brand names are not fully standardized, so some brand counts are split across spellings.
- The removal date column contains an impossible year (2103), which looks like a data-entry error and should be ignored when reading removal trends.
- Records by year reflect when companies reported, not when products were sold.

---

## 📁 Large Files (not uploaded to GitHub due to size)

| File | What it is | Link |
|---|---|---|
| `cscpopendata.csv` | Raw dataset | [Download](https://1drv.ms/x/c/f2e0a4c9963077ba/IQBLTWHrfnWdQZrTymjOdt7_ATNecGZfKx6U0BYNTh9lwKY?e=OdTvIs) |

Download the file and save it in the project folder before running the notebook.

---

The raw dataset is linked in the Large Files section above.
