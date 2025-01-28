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

   Identify trends or patterns in Health indicators (e.g.,Blood pressure changes) between smokers and non-smokers.

  ### **Data Analysis **

  include some intresting codes worked with
  
    ```SQL
   SELECT  Age , Sex , Heart_rate , Chol
  From smokers_health.smoking_health_data_final where Age between 35 and 55;
   ```

     ```SQL
     SELECT Distinct  max(Age) as Max_Age , sex
    FROM smokers_health.smoking_health_data_final Group by sex Having max(Age);
     ```
