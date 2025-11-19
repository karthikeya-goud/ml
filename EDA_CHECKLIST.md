# 📊 Master EDA Checklist for Any Dataset

> This checklist is designed to guide Exploratory Data Analysis (EDA) for **numerical, categorical, and time-series features**. It also provides **algorithm-specific requirements**, alternatives, and best practices. Tick ✅ each step as you complete it.

---

## 0️⃣ General Dataset Overview
- [X] Load dataset (`df.head()`, `df.info()`)  
- [ ] Check dataset shape (rows, columns)  
- [ ] Identify feature types: numerical, categorical, date/time  
- [ ] Check target variable type: regression (numeric) / classification (categorical)  
- [ ] Check missing values summary (`df.isna().sum()`)  

---

## 1️⃣ Numerical Features

### 1.1 Summary Statistics
- [ ] Mean, Median, Mode  
- [ ] Standard deviation, Variance  
- [ ] Min, Max, Range  
- [ ] Skewness, Kurtosis  

### 1.2 Distribution Analysis
- [ ] Histogram / KDE plots  
- [ ] Boxplot / Violin plot  
- [ ] Identify multi-modality  

### 1.3 Outlier Detection
- [ ] IQR method  
- [ ] Z-score method  
- [ ] Visual inspection (boxplot / scatterplot)  
- [ ] **Alternative** if too many outliers: Robust Scaling, Winsorization  

### 1.4 Scaling / Normalization
**Required for:** Linear models, Distance-based models (KNN, SVM), Neural Networks  
- [ ] StandardScaler  
- [ ] MinMaxScaler  
- [ ] RobustScaler (if outliers present)  

### 1.5 Correlation & Multicollinearity
- [ ] Pearson correlation (numeric-numeric)  
- [ ] Spearman correlation (monotonic)  
- [ ] Multicollinearity check (VIF)  
- [ ] **Alternative:** PCA / remove highly correlated features  

---

## 2️⃣ Categorical Features

### 2.1 Frequency & Distribution
- [ ] Value counts / percentage  
- [ ] Bar plot / Count plot  
- [ ] Detect rare categories  

### 2.2 Missing Values
- [ ] Count missing per category  
- [ ] **Alternative:** Add 'Missing' category / Impute most frequent  

### 2.3 Cardinality
- [ ] Check number of unique categories  
- [ ] **Alternative:** Group rare categories / Target encoding  

### 2.4 Encoding
- [ ] One-hot encoding (linear models, distance-based models)  
- [ ] Label encoding (trees, gradient boosting)  
- [ ] **Alternative:** Embedding for high-cardinality categorical features  

---

## 3️⃣ Time-Series / Date Features

### 3.1 Date Parsing & Feature Extraction
- [ ] Convert to datetime  
- [ ] Extract: year, month, day, weekday, hour, quarter  

### 3.2 Trend & Seasonality
- [ ] Plot rolling mean & variance  
- [ ] Decompose series into trend, seasonality, residual  

### 3.3 Missing Values
- [ ] Interpolate missing points  
- [ ] Forward/backward fill  

### 3.4 Visualization
- [ ] Line plot over time  
- [ ] Seasonal plots (month/day vs target)  
- [ ] Autocorrelation / Lag plots (for regression models)  

---

## 4️⃣ Target Variable Analysis

### 4.1 Regression Target
- [ ] Distribution check (histogram, KDE)  
- [ ] Outlier detection  

### 4.2 Classification Target
- [ ] Check class balance (`value_counts()`)  
- [ ] Bar plot  
- [ ] **Alternative if imbalanced:** SMOTE, undersampling, oversampling  

### 4.3 Feature vs Target
- [ ] Numerical vs target: scatter plot, correlation, boxplot  
- [ ] Categorical vs target: groupby mean, boxplot / violin plot  

---

## 5️⃣ Algorithm-Specific EDA Requirements

| Algorithm Type | Numerical Outliers | Scaling | Skewness Transform | Categorical Encoding | Multicollinearity | Missing Values |
|----------------|-----------------|--------|-----------------|-------------------|-----------------|----------------|
| **Linear Regression** | ✅ Mandatory | ✅ Mandatory | ✅ Recommended | One-hot / Dummy | ✅ Check & handle | ✅ Impute / handle |
| **Logistic Regression** | ✅ Mandatory | ✅ Mandatory | ✅ Recommended | One-hot / Dummy | ✅ Check & handle | ✅ Impute / handle |
| **SVM** | ✅ Mandatory | ✅ Mandatory | ✅ Optional | One-hot / Label | ❌ Usually ignored | ✅ Impute / handle |
| **KNN** | ✅ Mandatory | ✅ Mandatory | ✅ Optional | One-hot / Dummy | ❌ Usually ignored | ✅ Impute / handle |
| **Neural Networks** | ✅ Mandatory | ✅ Mandatory | ✅ Optional | One-hot / Embeddings | ❌ Usually ignored | ✅ Impute / handle |
| **Decision Trees** | ❌ Optional | ❌ Not required | ❌ Not required | Label / One-hot | ❌ Not required | ✅ Handle missing |
| **Random Forest / XGBoost / LightGBM** | ❌ Optional | ❌ Not required | ❌ Not required | Label / One-hot | ❌ Not required | ✅ Handle missing |
| **K-Means / Clustering** | ✅ Mandatory | ✅ Mandatory | ✅ Optional | One-hot / Dummy | ❌ Usually ignored | ✅ Impute / handle |

> ✅ = Compulsory  
> ❌ = Optional  

---

## 6️⃣ Additional Notes / Alternatives

- **Too many outliers:** Use RobustScaler or Winsorization instead of removing  
- **Highly skewed features:** Log / Box-Cox / Yeo-Johnson transform  
- **High-cardinality categorical features:** Target encoding or embeddings  
- **Imbalanced classification target:** SMOTE, ADASYN, undersampling  
- **Multicollinearity:** Remove correlated features or use PCA / regularization (Ridge, Lasso)  
- **Large dataset visualization:** Sample for plotting to reduce memory issues  

---

## 7️⃣ Final Steps

- [ ] Summarize EDA insights  
- [ ] Decide on feature transformations (scaling, encoding, transformations)  
- [ ] Handle missing values / outliers based on target algorithm  
- [ ] Document assumptions, challenges, and solutions  

---

# ✅ Usage Instructions

1. Open this Markdown file in VS Code or GitHub.  
2. Tick ✅ each checkbox as you complete the EDA step.  
3. Follow the **algorithm-specific guidance** in Section 5.  
4. Use **alternatives** in Section 6 if standard approach is not suitable.  
5. After completing, you will have a **clean, ready-to-use dataset** for any regression or classification model.

---

