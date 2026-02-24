# Blood Transfusion Service Center Dataset

## Dataset Overview

The Blood Transfusion Service Center dataset contains historical donation records of blood donors. Each record represents a donor and includes information about their past blood donation behavior. The dataset contains 748 records with 5 features:

Recency: Months since last donation    
Frequency: Total number of donations                        
Monetary: Total blood donated (c.c.)                       
Time: Months since first donation                      
Class: Target variable whether the donor donated in March 2007 (1 = Yes, 0 = No) 

## 1. Univariate Analysis
- Continuous features are recency, monetary, and time were visualized using histograms with KDE.  
- Discrete features frequency were visualized using countplots.  
- Target variable class was visualized with a countplot to show the balance of the classes.

## 2. Distribution of Monetary (Revenue)
- The monetary column was plotted using a histogram and boxplot to observe the distribution and detect potential outliers.

## 3. Bivariate Analysis
- Relationships between features and the target were explored using boxplots, violin plots, and scatterplots.  

## 4. Correlation Matrix
- A heatmap of correlations among numerical features was created that helps identify linear relationships between features and potential multicollinearity before modeling.

## 5. Time-Based Analysis
- Scatterplots were used to explore patterns over time, that helps understand how past donation patterns relate to the likelihood of future donation.

