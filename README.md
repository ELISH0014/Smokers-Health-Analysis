# Smokers Health Analysis

### Project Overview 
This project , Smoking Health Analysis, explores the relationship between smoking Habits and their impact on Health indicators using a Data set of individuals. 
The Analysis focuses on metrics such as Age, Gender , Smoking status , Heart rate , Blood pressure , Cholesterol levels and Daily cigarette consumption using 
SQL and Tableau.
It demonstrates the use of structured Data Analysis to uncover trends and relationships, providing a foundation for further research into the impact of smoking on health . 

### Tools 

- Excel & Googlesheets - Data cleaning , Automation.
   -  [Download here](https://docs.google.com/spreadsheets/d/1yW2vk4i6eSYC_i-99tccJcaSP3x955sfhmsll1ssY1I/edit?usp=sharing)
- SQL- Data Analysis
- Tableau - Visualization 

### Data cleaning / Preparation 

In the initial Data preparation phase , I performed the following task :
- **Data Loading and inspection,**
- **Handling Missing values.**
- **Data cleaning and formatting**.

   ### Data Exploration

   **1**. **Distribution of Smoking Habits** :

   Analyzes the Frequency and Pattern of Smoking behaviour among
   different Demographic groups
    e.g (Age , Gender).
  
    **2**.**Correlation Analysis** :

   Investigate the relationship between Smoking status and Health indicators such as Heart Rate, Blood Pressure , and Cholesterol levels.

    **3.** **Impact of Cigarette Consumption** :
 
  Examine How daily cigarette consumption influences  specific health metrics over time .

    **4.** **Trend Analysis :**

   Identify Trends / Patterns in Health indicators (e.g.,Blood pressure changes) between smokers and non-smokers.
  ![ABNORMAL(HIGH)](https://github.com/user-attachments/assets/16958d12-1727-4272-b836-3f210470393c)
  

  


  ### **Data Analysis **

  include some intresting codes worked with
  
    ```SQL
   Select  Age , Sex , Heart_rate , Chol
  From smokers_health.smoking_health_data_final where Age between 35 and 55;
   ```

     ```SQL
     SELECT Distinct  max(Age) as Max_Age , sex
    FROM smokers_health.smoking_health_data_final
     Group by sex Having max(Age);
     ```
```SQL
Select Age , cigs_per_day , chol , heart_rate
FROM smokers_health.smoking_health_data_final
where chol between 200 and 239 and heart_rate >100; 
```

```SQL
Select  sum(Heart_rate) as Total_outliers_HeartRate , 
 count(*) as outlier_count, avg(heart_rate) as AVG_Outlier_heartrate 
 FROM  smokers_health.smoking_health_data_final
 where chol between 200 and 239 and heart_rate >100;
```

```SQL
Select Heart_rate , cigs_per_day , chol, 
 count(*) over () as total_count 
 from smokers_health.smoking_health_data_final 
 where 
 chol >=240;
```

```SQL
select Age , sex , current_smoker, Heart_rate , Blood_pressure, 
cigs_per_day, chol,
case 
when cigs_per_day = null then 'unknown'
when  cigs_per_day = 0 then 'Non-Smoker'
when cigs_per_day between 1 and 5 then 'Occasional smoker ' 
when cigs_per_day between 6 and 15  then ' Moderate smoker '
when cigs_per_day >=16 then 'Heavy smoker'
else 'unknown'
End as smokers_frequency
from smokers_health.smoking_health_data_finaL;
```

```SQL
select  current_smoker ,  count(*) as total_individuals, 
avg(Heart_Rate) as Mean_Heart_Rate , min(Heart_rate) AS Min_Heart_Rate , 
max(Heart_rate) as max_Heart_rate 
from smokers_health.smoking_health_data_finaL 
group by current_smoker;
```

 ```SQL
select case 
when Age < 20 then '<20'
when Age between 20 and 39 then '20-39'
when age between 40 and 59 then '40-59'
else '60+'
end as Age_Group ,
count(*) as total_individuals, 
avg(Heart_Rate) as Mean_Heart_Rate , min(Heart_rate) AS Min_Heart_Rate , 
max(Heart_rate) as max_Heart_rate 
from smokers_health.smoking_health_data_finaL 
group by 
case 
when Age < 20 then '<20'
when Age between 20 and 39 then '20-39'
when age between 40 and 59 then '40-59'
else '60+'
END;
```
         
