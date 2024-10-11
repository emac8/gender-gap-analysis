# Gender Pay Gap Analysis

## Overview
This project presents a visual analysis of the gender pay gap across different periods, career stages, and occupations. The graphs highlight both the historical shifts in the gender pay gap and the differences in wages between male- and female-dominated occupations.

## Graphs and Analysis

**Gender Pay Across Industries(Top 10)**
This visualization highlights significant gender pay disparities across different industries, with some sectors showing more pronounced gaps than others. ![Gender Pay Across Industries](https://github.com/JMiceli7/gender-gap-analysis/blob/main/Project%204%20Graphics/male_to_female_salary_ratio.png)

**Gender Pay Across Industries**
This visualization highlights income inequality across industries, showing not only the pay gap but also how significant it is within various sectors.
![Gender Pay Across Industries interactive plot version](https://github.com/JMiceli7/gender-gap-analysis/blob/main/Project%204%20Graphics/interactive_plot.html) 
![Gender Pay Across Industries png version](https://github.com/JMiceli7/gender-gap-analysis/blob/main/Project%204%20Graphics/Gender%20Pay%20by%20Industry%20dot%20plot.png)

**Gender Pay Across Region & Race** 
This heatmap provides a clear visual comparison of how income varies by race and region, highlighting disparities and patterns in economic outcomes across different demographic groups. ![Gender Pay Across Region & Race](https://github.com/JMiceli7/gender-gap-analysis/blob/main/Project%204%20Graphics/mean_income_by_region_and_race.png)


 **Gender Pay Gap Over Time (1981-2013)**  
   This graph illustrates the historical changes in the gender pay gap over the period from 1981 to 2013. It shows how the gap between male and female salaries has fluctuated, with notable periods of improvement and plateaus. The most significant reduction in the gap occurred between 2009 and 2011, but disparities still remain.
![Gender Pay Gap Over Time](https://github.com/JMiceli7/gender-gap-analysis/blob/main/Project%204%20Graphics/pay_gap_over_time.png)

 **Average Wage by Age Bracket and Gender**  
   This graph breaks down the gender pay gap by age group, showing how the disparity grows as individuals age. It reveals that women earn progressively less compared to men as they advance in their careers, particularly in the 40-50 and 50+ age brackets.
   ![Average Wage by Age Bracket and Gender](https://github.com/JMiceli7/gender-gap-analysis/blob/main/Project%204%20Graphics/bar_gap_ages.png)

 **Average Wage by Occupation (Top Occupations for Women)**  
   This graph focuses on the average wages for women in occupations where they are overrepresented, such as nursing, teaching, and secretarial roles. It shows that women are often concentrated in lower-paying jobs, despite the importance of many of these roles.
   ![Average Wage by Occupation (Top Occupation for Women](https://github.com/JMiceli7/gender-gap-analysis/blob/main/Project%204%20Graphics/women_occ.png)

 **Average Wage by Occupation (Top Occupations for Men)**  
   This graph presents the average wages for men in male-dominated occupations like management, construction, and sales. It demonstrates that men tend to dominate higher-paying roles, contributing to the overall wage disparity.
   ![Average Wage by Occupation (Top Occupation for Men](https://github.com/JMiceli7/gender-gap-analysis/blob/main/Project%204%20Graphics/men_occ.png)

**Machine Learning Application: Randomforest Regressor Model**

   A random forest regressor model was used in an attempt to build a model capable of predicting the pay gap between male and female salaries given a set of input features. Randomforest regressor was chosen for multiple reasons: a regression model was better suited the needs of this project compared to a classifier model, as we were looking to make predicitons for a continuous variable, not to make predictions of the placement of a sample into one or another classes. Randomforest also had advantages to other regression models. Linear regressions are sensitive to outliers in the data set and decision tree modeling can lead to overfitting. 
   
   The first iteration of the model utiulized multiple input features: year, state name, race, age, union type, marital status, and sex. To build the mode, average income was computed as grouped by the previously named features. The data was pivoted to generate separate average incomes for male and female while still grouped by the input features. This let us create a column listed "pay_gap" and we were able to compute the pay gap between each set of male/female salaries in our reshaped data set. 
   
   One-hot-encoding was then used on the categorial features of state name, race, union type, and marital status. The data was then ready for spliting and training. 
   
![One-Hot_Encoding](https://github.com/JMiceli7/gender-gap-analysis/blob/main/Project%204%20Graphics/one_hot_encoding.png)

   The target vector, "pay_gap" was separated from the remaining columns used for features.    

![Separating_features_target_vector](https://github.com/JMiceli7/gender-gap-analysis/blob/main/Project%204%20Graphics/separated_features_target_vector.png)

   Standard scaler was used to ensure the data could be within the same scale and easily comparable. 
   
![Standard Scaler](https://github.com/JMiceli7/gender-gap-analysis/blob/main/Project%204%20Graphics/standard_scaler.png)
   
   Train, test, split method was used to create a training and test data set. 

![Train_Test_Split](https://github.com/JMiceli7/gender-gap-analysis/blob/main/Project%204%20Graphics/train_test_split.png)
   
   The randomforest regression model was then initiated. Our evaluation report revealed a high accuracy at R-Squared = 0.8439 but a Mean Squared Error (MSE) of 10150.0645.

![Initialize RandomForest Model](https://github.com/JMiceli7/gender-gap-analysis/blob/main/Project%204%20Graphics/randomforest_regressor_model_initialization.png)

![First Iteration Results](https://github.com/JMiceli7/gender-gap-analysis/blob/main/Project%204%20Graphics/first_iteration_model_results.png)

   To improve the accuracy and performance of the model, the previous process was completed again, this time with a reduced number of features. To determine which features were most valuable from the first model, a feature importance method was used.
   
![Top 10 Feature Importance Analysis](https://github.com/JMiceli7/gender-gap-analysis/blob/main/Project%204%20Graphics/Regression%20Model%20top%2010%20features.png)
   
   We found that there were mainly 3 variables that seemed to have the biggest influence on the model: year, age, and sex (male and female). With this inforamtion, the model was remade with the fewer features. This had a substancial improvement on the performance of our model. We achieved an R-Squared value of 0.92405 and a MSE of only 8.0346. We now have a model that can accuarately predict the pay gap for this given set of input features.

![Final Model Iteration Results](https://github.com/JMiceli7/gender-gap-analysis/blob/main/Project%204%20Graphics/improved_model_results.png)

![Limited Features Importance Analysis](https://github.com/JMiceli7/gender-gap-analysis/blob/main/Project%204%20Graphics/Regression%20Model%20limited%20features.png)

   This model can be used in many important ways. One of the most important uses is its ability to help us observe pay gap trends over time. It will also allow us to evaluate policy measures that have taken affect. As more data is collected, our model can continue to grow and its precictions continued to be evaluated as a marker of progress. We can also play with adding more input features such as additional demographic information in hopes to make even more comparisons, potentially at the sacrifice of accuracy but this could continue to be evaluated. FInally, we can also simulate changes and reflect the difference made in pay gap prediction. Using future year projections, manipulating higher female salaries, higher male salaries, a balance of additions to both, percentage additions of either or, etc. 
