# LendingClub_loan_default_prediction
The study analyses the relationship between the probability of default of a loan and the customer demographics and the market penetration of Lending Club within the United States, which is a peer to peer lender headquartered in San Francisco, California. The analysis is performed using the 2016-2017 fiscal year data from Lending Club.

Importance of problem statement:
Loan defaults are the primary contributors to losses incurred by the financial organization. A loan approval depends on multiple criteria, some of which being – customer credit grading, annual income etc. An analysis would help us establish the relationship between the various factors and the probability of default. This would help us understand which of these factors predominantly affect the probability of default of each customer and thereby help minimize our losses due to unrecovered investments.
Summary of procedure and results:
As a part of our analysis, we explored multiple 1:1 relationships between the variables to understand how the variation in one of them affects the others. Also, we have categorized the customer base penetration for Lending Club across the United States. The following data manipulation, statistical techniques and visualization methods were implemented to perform the analysis and derive the results:
1.	Data importing and cleaning
2.	Descriptive statistics 
3.	Merging multiple data files
4.	Categorization based on loan types for following measures:
o	Number of defaulters
o	Revenue per loan
5.	Interactive map of the United States using Bokeh to showcase the state-wise distribution of:
o	Percentage of defaulters
o	Number of customers
6.	Logistic regression
7.	Calculation of probability of defaults using the coefficients of logistic regression
From the above-mentioned analyses, we derived that the probability of defaults is proportional to the below mentioned variables:
-	Debt to income ratio (DTI)
-	Interest rate
-	Term of loan
-	Employment length
-	Credit score category for the customer
Also, from the interactive map of United States, we could generate the following insights:
-	Low presence of Lending Club in the states with less corporate footprint.
-	No presence in the state in Iowa.
Background:
While researching on the methodologies to be followed for our analyses, we came across several studies conducted on similar lines. Most of the studies used logistic regression to calculate the probability, along with further refinement using several advanced machine learning techniques such as multiple discriminant analysis, random forest, support vector machine, etc. Depending on the nature of the study, some of the studies had performed operations on a large dataset, whereas some had smaller datasets. However, we also noticed that the studies were quite specific on the type of loan default for which the prediction was done, i.e., mortgage, vehicle loan etc. Our analysis incorporated a holistic approach with multiple loan categories taken consideration.
Computational Steps:
For our analysis, we used the following steps:
1)	Data import and cleaning: The data was sourced from Kaggle (also available in the Lending Club website) and comprised of the 2016-2017 Fiscal Year loan data for Lending Club. Then we imported the required columns and used functions to convert the column data into the required datatype. For example, employee length was converted from string to numeric using ‘string.split’ function. We also added a column to compute the revenue per customer. 
2)	Merging multiple data files: Next we aggregated another dataset containing zip code details and included the population segregated by zip code to merge the two datasets together. 
3)	Descriptive Statistics:
 
