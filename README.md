# Smoking Health Analysis

## Project Overview
This project, Smoking Health Analysis, explores the relationship between smoking habits and their impact on cardiovascular health indicators using a dataset of individuals.

The analysis focuses on metrics such as age, gender, smoking status, heart rate, blood pressure, cholesterol levels, and daily cigarette consumption.

Using SQL and Tableau, the project identifies patterns and relationships between smoking behavior and health outcomes, providing insights into cardiovascular risk factors.

---

## Tools Used
- Excel / Google Sheets — Data cleaning and preparation  
- SQL — Data analysis and transformation  
- Tableau — Data visualization  

Dataset:
https://docs.google.com/spreadsheets/d/1yW2vk4i6eSYC_i-99tccJcaSP3x955sfhmsll1ssY1I/edit?usp=sharing

---

## Data Cleaning and Preparation
The following steps were performed:
- Data loading and inspection  
- Handling missing values  
- Data cleaning and formatting  
- Standardizing categorical variables  

---

## Data Exploration

### Smoking Habit Distribution
Analyzed smoking patterns across age and gender groups.

### Correlation Analysis
Investigated relationships between smoking status and health indicators:
- Heart rate  
- Blood pressure  
- Cholesterol levels  

### Cigarette Consumption Impact
Examined how daily cigarette consumption affects cardiovascular health indicators.

### Trend Analysis
Identified patterns in health indicators between smokers and non-smokers, including cholesterol categories:
- Normal
- Borderline
- High

---

## SQL Analysis

### 1. Age-based filtering
```sql
SELECT Age, Sex, Heart_rate, Chol
FROM smokers_health.smoking_health_data_final
WHERE Age BETWEEN 35 AND 55;
2. Maximum age by gender
SELECT DISTINCT MAX(Age) AS Max_Age, Sex
FROM smokers_health.smoking_health_data_final
GROUP BY Sex;
3. Age, cigarettes, cholesterol and heart rate filter
SELECT Age, cigs_per_day, Chol, Heart_rate
FROM smokers_health.smoking_health_data_final
WHERE Chol BETWEEN 200 AND 239
AND Heart_rate > 100;
4. Outlier analysis (heart rate)
SELECT  
    SUM(Heart_rate) AS Total_outliers_HeartRate,
    COUNT(*) AS outlier_count,
    AVG(Heart_rate) AS avg_outlier_heart_rate
FROM smokers_health.smoking_health_data_final
WHERE Chol BETWEEN 200 AND 239
AND Heart_rate > 100;
5. High cholesterol group analysis
SELECT Heart_rate, cigs_per_day, Chol,
    COUNT(*) OVER () AS total_count
FROM smokers_health.smoking_health_data_final
WHERE Chol >= 240;
6. Smoking frequency classification
SELECT 
    Age,
    Sex,
    current_smoker,
    Heart_rate,
    Blood_pressure,
    cigs_per_day,
    Chol,
    CASE 
        WHEN cigs_per_day IS NULL THEN 'Unknown'
        WHEN cigs_per_day = 0 THEN 'Non-Smoker'
        WHEN cigs_per_day BETWEEN 1 AND 5 THEN 'Occasional Smoker'
        WHEN cigs_per_day BETWEEN 6 AND 15 THEN 'Moderate Smoker'
        WHEN cigs_per_day >= 16 THEN 'Heavy Smoker'
        ELSE 'Unknown'
    END AS smoking_frequency
FROM smokers_health.smoking_health_data_final;
7. Smoking group summary
SELECT  
    current_smoker,
    COUNT(*) AS total_individuals,
    AVG(Heart_rate) AS mean_heart_rate,
    MIN(Heart_rate) AS min_heart_rate,
    MAX(Heart_rate) AS max_heart_rate
FROM smokers_health.smoking_health_data_final
GROUP BY current_smoker;
8. Age group analysis
SELECT  
    CASE 
        WHEN Age < 20 THEN '<20'
        WHEN Age BETWEEN 20 AND 39 THEN '20-39'
        WHEN Age BETWEEN 40 AND 59 THEN '40-59'
        ELSE '60+'
    END AS Age_Group,
    COUNT(*) AS total_individuals,
    AVG(Heart_rate) AS mean_heart_rate,
    MIN(Heart_rate) AS min_heart_rate,
    MAX(Heart_rate) AS max_heart_rate
FROM smokers_health.smoking_health_data_final
GROUP BY 
    CASE 
        WHEN Age < 20 THEN '<20'
        WHEN Age BETWEEN 20 AND 39 THEN '20-39'
        WHEN Age BETWEEN 40 AND 59 THEN '40-59'
        ELSE '60+'
    END;
9. Cholesterol level grouping
SELECT  
    current_smoker AS CURRENT_SMOKER,
    CASE 
        WHEN Chol < 200 THEN 'NORMAL'
        WHEN Chol BETWEEN 200 AND 239 THEN 'BORDERLINE'
        ELSE 'HIGH'
    END AS CHOLESTEROL_LEVELS,
    COUNT(*) AS total_individuals,
    AVG(Heart_rate) AS mean_heart_rate,
    MIN(Heart_rate) AS min_heart_rate,
    MAX(Heart_rate) AS max_heart_rate
FROM smokers_health.smoking_health_data_final
GROUP BY 
    current_smoker,
    CASE 
        WHEN Chol < 200 THEN 'NORMAL'
        WHEN Chol BETWEEN 200 AND 239 THEN 'BORDERLINE'
        ELSE 'HIGH'
    END;

## Visual Insights

ABNORMAL(HIGH) (1).png
## Key Insights

- Smokers consistently show higher heart rates than non-smokers  
- Cholesterol levels significantly influence cardiovascular risk  
- Heavy smokers exhibit the most unstable health indicators  
- Smoking combined with high cholesterol increases health risk severity  
---

## Conclusion

Smoking has a strong negative impact on cardiovascular health indicators.

The analysis shows that smoking increases heart rate and worsens cholesterol-related risk, especially in individuals with existing cholesterol abnormalities.

Smoking is a major modifiable risk factor for cardiovascular disease.
