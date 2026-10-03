# Data Cleaning Log

Generated: 2026-10-03 10:00:00

✓ Loaded data/raw.csv: 100 rows × 12 columns

### Issues Identified ###

**Missing Values:**
  - Age: 3 rows (3.0%)
  - Cabin: 77 rows (77.0%)
  - Embarked: 2 rows (2.0%)

**Duplicate Rows:** 0

**Data Types:**
  - PassengerId: int64
  - Survived: int64
  - Pclass: int64
  - Name: object
  - Sex: object
  - Age: float64
  - SibSp: int64
  - Parch: int64
  - Ticket: object
  - Fare: float64
  - Cabin: object
  - Embarked: object

**Column Names:** PassengerId, Survived, Pclass, Name, Sex, Age, SibSp, Parch, Ticket, Fare, Cabin, Embarked

### Cleaning Steps ###

1. Standardizing column names to snake_case...
2. Trimming whitespace from text fields...
3. Converting placeholder values to NaN...
4. Removing duplicate rows...
   Removed 0 duplicate rows
5. Converting data types...
6. Handling missing values...
   - Dropped 'cabin' column (77.0% missing)
   - Filled 'age' with median: 28.0
   - Filled 'embarked' with mode: S
7. Checking outliers (IQR method - kept as they are genuine)...
   - Age: 12 outliers detected (kept)

✓ Cleaning complete: 100 rows × 12 cols → 100 rows × 11 cols

✓ Saved cleaned data: data/cleaned.csv
✓ Saved cleaning log: cleaning_log.md
