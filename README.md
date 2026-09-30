[README (3).md](https://github.com/user-attachments/files/32857248/README.3.md)
# 🧹 SWYNEX Data Analysis: Data Cleaning & Preparation

Cleaning a raw public dataset so it is ready for analysis, using **Python (pandas)** and a browser-based tool, **Data Cleaning Studio**.

🌐 **Live app:** [Open Data Cleaning Studio](https://JDSALAGALA.github.io/SWYNEX-Data-Analysis/)
💼 **LinkedIn post:** [See the project post](https://lnkd.in/p/dsus8Qdu)
📂 **Dataset:** Titanic passenger data ([source](https://github.com/datasciencedojo/datasets))

---

## 📌 Project Overview

Raw data is rarely ready to analyse. This project takes a public dataset and:

1. **Identifies** missing values, duplicate records, incorrect data types and inconsistent values
2. **Cleans** the data with a reproducible Python script
3. **Documents** every change in an automatically generated log
4. **Provides** a web app that does the same profiling and cleaning on any CSV

## 🗂️ Repository Structure

```
SWYNEX-Data-Analysis/
├── data/
│   ├── raw.csv            # Original, untouched dataset
│   └── cleaned.csv        # Cleaned dataset
├── clean_data.py          # Python cleaning pipeline
├── requirements.txt       # Python dependencies
├── cleaning_log.md        # Auto-generated log of issues and actions
├── index.html             # Data Cleaning Studio web app
├── linkedin/              # Project visuals (PNG + SVG)
└── README.md
```

## 🔍 Issues Identified

> Figures below are for the raw Titanic file (891 × 12). Confirm them against `cleaning_log.md` after running the script.

| Issue Type | Findings |
|---|---|
| **Missing values** | `age` (177 rows, ~19.9%), `cabin` (687 rows, ~77.1%), `embarked` (2 rows) |
| **Duplicate records** | 0 exact duplicate rows (every `PassengerId` is unique) |
| **Incorrect data types** | `survived` and `pclass` stored as integers but are categories |
| **Inconsistent values** | Mixed-case / camelCase column names (`PassengerId`, `SibSp`); text fields checked for whitespace and case variants |

## 🛠️ Cleaning Steps

| # | Step | Detail |
|---|---|---|
| 1 | Standardise column names | Converted to `snake_case` |
| 2 | Trim whitespace | Removed leading/trailing spaces in text cells |
| 3 | Handle placeholders | `''`, `?`, `N/A` converted to proper nulls |
| 4 | Remove duplicates | Dropped exact duplicate rows |
| 5 | Fix data types | Numeric, datetime and categorical conversions |
| 6 | Handle missing values | Dropped `cabin` (>60% empty); `age` filled with median; `embarked` filled with most common port |
| 7 | Check outliers | Flagged with the IQR rule but **kept** (they are genuine values) |

**Result:** `891 rows × 12 columns` (raw) → `891 rows × 11 columns` (cleaned)

## 🚀 How to Run

### Python script
```bash
pip install -r requirements.txt
python clean_data.py                 # uses the Titanic dataset by default
python clean_data.py my_file.csv     # or any CSV file / URL
```
Outputs `data/raw.csv`, `data/cleaned.csv` and `cleaning_log.md`.

### Web app
Open the [live app](https://JDSALAGALA.github.io/SWYNEX-Data-Analysis/), or open `index.html` locally, then:
1. Upload a CSV (or try the built-in messy sample)
2. Review the issues found
3. Choose the cleaning actions to apply
4. Download `cleaned.csv` and `cleaning_log.md`

Everything runs in your browser, and no data is uploaded anywhere.

## ✨ Web App Features

- Drag-and-drop CSV upload
- Automatic profiling: missing values, duplicates, data types, inconsistent text
- Toggle each cleaning action on or off
- Before/after statistics and a readable change log
- Export of cleaned data and log
- Light and dark theme support

## 🧰 Tech Stack

`Python` · `pandas` · `HTML/CSS/JavaScript` · `Git & GitHub`

## ⚠️ Assumptions & Limitations

- Median imputation for `age` keeps the mean stable but reduces variance. A group-wise median (by `pclass` and `sex`) would be a better refinement.
- High `fare` values were kept because they correspond to real first-class tickets.
- The web app detects date and number columns heuristically, so review results on unusual formats.

## 🔮 Future Improvements

- Charts of missing values per column
- Group-wise imputation options
- Support for Excel files

## 👤 Author

**JDSALAGALA**
[LinkedIn](https://www.linkedin.com/in/salagala-j-d-massilie-161265371) · [GitHub](https://github.com/JDSALAGALA)

---
⭐ If you found this useful, consider starring the repo!
