# 💄 Chemicals in Cosmetics Analysis Project

> **Python | Pandas | Seaborn** — Analyzed 114,000+ cosmetic product records to find which chemicals are used most, which categories, companies, and brands report the most, and how reporting changed over time.

---

## 📌 Project Overview

This project explores the **California Safe Cosmetics Program (CSCP)** open dataset, which lists cosmetic products sold in California that contain chemicals linked to cancer, birth defects, or other reproductive harm.

The goal is to turn raw regulatory data into clear insights about chemical usage, product categories, company and brand activity, and reporting trends over the years.

---

## 🎯 Objectives

- Clean the raw data (duplicates, missing values, wrong data types)
- Understand how products and chemicals are distributed across categories
- Identify the most frequently reported chemicals, companies, and brands
- Study reporting trends and chemical removals over time
- Build simple KPIs to track chemical use, product variety, and company activity

---

## 📂 Dataset

| Detail | Value |
|---|---|
| Source | California Safe Cosmetics Program (CDPH) open data |
| File | `cscpopendata.csv` ([Download here](https://1drv.ms/x/c/f2e0a4c9963077ba/IQBLTWHrfnWdQZrTymjOdt7_ATNecGZfKx6U0BYNTh9lwKY?e=OdTvIs)) |
| Raw size | 114,635 rows × 22 columns |
| After cleaning | 114,381 rows (254 duplicates removed) |

> ⚠️ The dataset is too large to upload to GitHub, so it is **not included in this repository**. Download it from the link above and place it in the project folder before running the notebook.

**Key columns:** `ProductName`, `CompanyName`, `BrandName`, `PrimaryCategory`, `SubCategory`, `ChemicalName`, `InitialDateReported`, `MostRecentDateReported`, `DiscontinuedDate`, `ChemicalDateRemoved`, `ChemicalCount`

---

## 🧹 Data Cleaning & Preparation

1. Checked shape, data types, null counts, and summary statistics
2. Removed **254 duplicate rows**
3. Filled missing `BrandName` values using the mode
4. Converted six date columns from text to `datetime`
5. Created new features: `Discontinued_Month`, `MostRecentDateReported_year`, and chemical update lag (`ChemicalUpdatedAt - ChemicalCreatedAt`)
6. Dropped columns not needed for analysis (`CSF`, `CSFId`, `CompanyId`, `PrimaryCategoryId`, `SubCategoryId`, `CasId`, `CasNumber`)

---

## ❓ Questions Answered

- How many products, companies, brands, and chemicals are reported?
- How are products distributed across primary categories and subcategories?
- What are the top 10 most used chemicals?
- Which companies and brands report the most products?
- How does product reporting change year by year?
- How often are chemical records updated?
- When were chemicals removed from products?
- Which category has the highest average chemical count per product?

---

## 🔍 Key Insights

- **33,716** unique products from **606** companies and **2,713** brands report **123** unique chemicals
- **Titanium dioxide** is by far the most reported chemical, with **93,000+ records**
- **Makeup Products (non-permanent)** make up the largest category with **75,800+ records**, followed by Nail Products and Skin Care Products
- Top subcategories are **Lip Color**, **Eye Shadow**, **Foundations and Bases**, **Nail Polish**, and **Lip Gloss**
- **L'Oréal USA**, **S+**, and **Coty** are the top reporting companies
- **Sephora**, **NYX**, and **bareMinerals** are the top reporting brands
- **Tattoos and Permanent Makeup** has the highest average chemical count per product (about 1.48)
- Reporting peaked in **2010** and again in **2013** and **2018**

---

## 🛠️ Tools & Libraries

| Tool | Purpose |
|---|---|
| Python | Core language |
| Pandas, NumPy | Data cleaning and analysis |
| Matplotlib, Seaborn | Visualization |
| Jupyter Notebook / Google Colab | Development environment |

---

## 📁 Repository Structure

```
Chemicals_in_Cosmetics_Analysis_Project/
│
├── Chemical_in_Cosmetic.ipynb    # Full analysis notebook
└── README.md                     # Project documentation
```

---

## ▶️ How to Run

1. Clone the repository
   ```bash
   git clone https://github.com/<your-username>/Chemicals_in_Cosmetics_Analysis_Project.git
   ```
2. Install the required libraries
   ```bash
   pip install pandas numpy matplotlib seaborn jupyter
   ```
3. Download `cscpopendata.csv` from [this link](https://1drv.ms/x/c/f2e0a4c9963077ba/IQBLTWHrfnWdQZrTymjOdt7_ATNecGZfKx6U0BYNTh9lwKY?e=OdTvIs) and save it in the project folder
4. Open `Chemical_in_Cosmetic.ipynb` in Jupyter or Google Colab
5. Update the file path in the data loading cell to point to `cscpopendata.csv`
6. Run all cells

---

## 💡 Recommendations

- Prioritize monitoring of **makeup and nail products**, which account for most chemical reports
- Track **titanium dioxide** use closely, since it appears in the vast majority of records
- Review **tattoo and permanent makeup** products, which carry the most chemicals per product on average
- Encourage consistent reporting across companies so year-over-year trends are comparable

---

## 👤 Author

**Your Name**
📧 your.email@example.com
🔗 [LinkedIn](https://linkedin.com/in/your-profile) | [GitHub](https://github.com/your-username)

---

⭐ If you found this project useful, please give it a star!
