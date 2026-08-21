# 🏥 Patient Health Records — Data Cleaning & Preprocessing

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python) ![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas) ![Scikit--learn](https://img.shields.io/badge/scikit--learn-Imputation-F7931E?logo=scikit-learn) ![Status](https://img.shields.io/badge/Project-Completed-success)

> A practical data-cleaning and preprocessing project on **50,000 patient health records**, focused on missing-value handling, outlier detection/treatment, and preparation for machine-learning workflows.
## 📄 Project Documentation

[👉 View / Download Project File](https://drive.google.com/file/d/1TNOrLpQKZKhUxAt-nRG7yp8Hqu35WkEO/view?usp=sharing)


## ✨ Project Overview

This project cleans and preprocesses a patient health dataset by identifying and handling missing values and outliers using different statistical techniques.

**Objective:** To clean and preprocess the patient health dataset by identifying and handling missing values and outliers using different statistical techniques, making the data suitable for machine learning and disease-risk prediction.

## 📊 Dataset

The notebook contains **50,000 rows × 9 columns**:

| Column | Description |
|---|---|
| `patient_id` | Patient identifier |
| `age` | Patient age |
| `gender` | Gender category |
| `region` | Region category |
| `bmi` | Body Mass Index |
| `blood_pressure` | Blood pressure measurement |
| `cholesterol` | Cholesterol measurement |
| `glucose` | Glucose measurement |
| `disease_risk` | Disease-risk indicator |

## 🔄 Project Workflow

```text
🏥 Patient Records → 🔍 Data Understanding → 🧩 Missing Values
        ↓
Mean/Median • Most Frequent • Random Sample • KNN • MICE
        ↓
🚨 Outlier Detection → Z-Score • IQR • Percentile
        ↓
🛡️ Winsorization → 📈 Before/After Comparison → ✅ Clean Dataset
        ↓
🤖 Machine Learning / Disease-Risk Prediction
```

## 🧩 Missing Value Techniques

### Simple Imputation — BMI

Mean and median strategies were explored for the numerical `bmi` column.

- **Mean:** average value.
- **Median:** middle value.

### Most Frequent Imputation — Region & Gender

Categorical missing values are replaced with the most frequently occurring category.

### Missing Indicator + Random Sample Imputation

A binary indicator records whether a value was originally missing, then random samples from available values are used for imputation.

### KNN Imputer

The notebook uses `KNNImputer(n_neighbors=5)` for `age`, `bmi`, `blood_pressure`, `cholesterol`, and `glucose`. Missing values are estimated from nearby/similar records.

### MICE

The notebook demonstrates **MICE (Multiple Imputation by Chained Equations)** using scikit-learn's `IterativeImputer`.

## 🚨 Outlier Detection & Treatment

### Z-Score

Used for `cholesterol` and `glucose`. Values with `|Z-score| > 3` are treated as outliers.

### IQR — BMI

```text
IQR = Q3 - Q1
Lower Fence = Q1 - 1.5 × IQR
Upper Fence = Q3 + 1.5 × IQR
```

The notebook identifies BMI observations outside these fences as outliers. Its recorded output identifies **322 BMI outliers**.

### Percentile Method

Numerical values are capped at the **1st and 99th percentiles** without deleting rows.

### Winsorization

Extreme BMI values are capped instead of removing complete patient records.

## 📈 Before vs After

The project compares dataset shape and summary statistics before and after outlier treatment. The notebook includes comparisons for Z-Score, IQR, percentile capping, and Winsorization.

## 🧪 YData Profiling

The notebook attempts to generate an automated profiling report with `ydata-profiling` covering dataset structure and exploratory analysis.

```python
from ydata_profiling import ProfileReport

profile = ProfileReport(
    data,
    title="Patient Health Records - Final Data Profiling",
    explorative=True
)

profile.to_file("patient_health_profiling.html")
profile.to_notebook_iframe()
```

## 🛠️ Technologies Used

- Python
- Jupyter Notebook
- NumPy
- Pandas
- SciPy
- Scikit-learn
- Matplotlib
- Seaborn
- YData Profiling

## ▶️ How to Run

```bash
git clone https://github.com/YOUR-USERNAME/Patient-Health-Records-Data-Cleaning.git
cd Patient-Health-Records-Data-Cleaning
pip install -r requirements.txt
jupyter notebook
```

Open **`Pr_2.ipynb`**. Place `patient_health_records_50000.csv` beside the notebook or update the CSV path in the loading cell.

## 📂 Repository Structure

```text
Patient-Health-Records-Data-Cleaning/
│
├── 📓 Pr_2.ipynb
│   └── Complete data cleaning & preprocessing notebook
│
├── 📄 README.md
│   └── Project documentation
│
└── 📊 patient_health_records_50000.csv
    └── Original patient health dataset
```

## 🎯 Project Outcome

**Missing Data → Imputation → Outlier Detection → Outlier Treatment → Comparison → Clean Dataset → Machine Learning Ready**

## 👨‍💻 Author

**Mahesh Lohar** — Data Cleaning & Preprocessing Project

> Note: The uploaded notebook contains a recorded Z-Score output of `(0, 13)`. Verify that cell after rerunning it before using that recorded number in a final presentation.
