# 🫁 Smoking Health Analysis

## 📌 Project Overview
This project, *Smoking Health Analysis*, explores the relationship between smoking habits and their impact on cardiovascular health indicators using a dataset of individuals.

The analysis focuses on key metrics such as:
- Age
- Gender
- Smoking status
- Heart rate
- Blood pressure
- Cholesterol levels
- Daily cigarette consumption

Using SQL and Tableau, this project identifies trends and relationships between smoking behavior and health outcomes, providing insights into cardiovascular risk factors.

---

## 🛠 Tools Used
- **Excel / Google Sheets** → Data cleaning and preprocessing  
- **SQL** → Data analysis and transformation  
- **Tableau** → Data visualization and dashboard creation  

Dataset:
[Google Sheets Data Source](https://docs.google.com/spreadsheets/d/1yW2vk4i6eSYC_i-99tccJcaSP3x955sfhmsll1ssY1I/edit?usp=sharing)

---

## 🧹 Data Cleaning & Preparation
During the data preparation phase, the following steps were performed:

- Data loading and initial inspection  
- Handling missing values  
- Data formatting and standardization  
- Verification of data consistency  

---

## 📊 Exploratory Data Analysis

### 1. Smoking Habit Distribution
Analyzed smoking patterns across demographic groups such as age and gender.

### 2. Correlation Analysis
Examined relationships between smoking status and health indicators including:
- Heart rate  
- Blood pressure  
- Cholesterol levels  

### 3. Cigarette Consumption Impact
Evaluated how daily cigarette consumption influences cardiovascular health metrics.

### 4. Trend Analysis
Identified patterns in health indicators between smokers and non-smokers, including cholesterol categories:
- Normal  
- Borderline (Abnormal)  
- High  

---

## 📸 Visual Insights

### Cholesterol & Heart Risk Categories

**High Risk (Abnormal)**
![High Risk](https://github.com/user-attachments/assets/16958d12-1727-4272-b836-3f210470393c)

**Borderline Cholesterol**
![Borderline](https://github.com/user-attachments/assets/2efd339a-4347-463c-9ca1-67b6c22fa59e)

**Normal Cholesterol**
![Normal](https://github.com/user-attachments/assets/8053d3c5-8c3a-4dd4-ab43-40d5b115337e)

---

## 🧠 SQL Analysis

### 1. Age-Based Filtering
```sql
SELECT Age, Sex, Heart_rate, Chol
FROM smokers_health.smoking_health_data_final
WHERE Age BETWEEN 35 AND 55;
