**Topic: Lending Portfolio Analysis of Lending Club**

**Introduction:**

**Problem statement:**

This study analyzes the relationship between the probability of default of a loan and the customer demographics and the market penetration of Lending Club within the United States, which is a peer to peer lender headquartered in San Francisco, California. The analysis is performed using the 2016-2017 fiscal year data from Lending Club.

**Importance of problem statement:**

Loan defaults are the primary contributors to losses incurred by the financial organization. A loan approval depends on multiple criteria, some of which being – customer credit grading, annual income etc. An analysis would help us establish the relationship between the various factors and the probability of default. This would help us understand which of these factors predominantly affect the probability of default of each customer and thereby help minimize our losses due to unrecovered investments.

**Summary of procedure and results:**

As a part of our analysis, we explored multiple 1:1 relationships between the variables to understand how the variation in one of them affects the others. Also, we have categorized the customer base penetration for Lending Club across the United States. The following data manipulation, statistical techniques and visualization methods were implemented to perform the analysis and derive the results:

1. Data importing and cleaning
2. Descriptive statistics
3. Merging multiple data files
4. Categorization based on loan types for following measures:
  - Number of defaulters
  - Revenue per loan
5. Interactive map of the United States using Bokeh to showcase the state-wise distribution of:
  - Percentage of defaulters
  - Number of customers
6. Logistic regression
7. Calculation of probability of defaults using the coefficients of logistic regression

From the above-mentioned analyses, we derived that the probability of defaults is proportional to the below mentioned variables:

- --Debt to income ratio (DTI)
- --Interest rate
- --Term of loan
- --Employment length
- --Credit score category for the customer

Also, from the interactive map of United States, we could generate the following insights:

- --Low presence of Lending Club in the states with less corporate footprint.
- --No presence in the state in Iowa.

**Background:**

While researching on the methodologies to be followed for our analyses, we came across several studies conducted on similar lines. Most of the studies used logistic regression to calculate the probability, along with further refinement using several advanced machine learning techniques such as multiple discriminant analysis, random forest, support vector machine, etc. Depending on the nature of the study, some of the studies had performed operations on a large dataset, whereas some had smaller datasets. However, we also noticed that the studies were quite specific on the type of loan default for which the prediction was done, i.e., mortgage, vehicle loan etc. Our analysis incorporated a holistic approach with multiple loan categories taken consideration.
**Computational Steps:**

For our analysis, we used the following steps:

1. 1) **Data import and cleaning** : The data was sourced from Kaggle (also available in the Lending Club website) and comprised of the 2016-2017 Fiscal Year loan data for Lending Club. Then we imported the required columns and used functions to convert the column data into the required datatype. For example, employee length was converted from string to numeric using &#39;string.split&#39; function. We also added a column to compute the revenue per customer.
2. 2) **Merging multiple data files** : Next we aggregated another dataset containing zip code details and included the population segregated by zip code to merge the two datasets together.
3. 3) **Descriptive Statistics** :<img src="https://github.com/sushil1792/LendingClub_loan_default_prediction/blob/master/Descriptive%20Statistics.png"/>
From the above table, we see that the mean interest rate that we are offering is 13.2% in 2016 and 2017. The average loan size that our bank offers is $14.7k. The median employment length of our customers was 6 years which had a median annual income of $95k. Also, our bank only offers loans for tenures of 3 and 5 years as evidenced from the table above.

1. 4) **Categorization based on loan types for following measures** :

Number of defaulters and revenue per loan: Next, we filtered the data according to the defaulters and grouped the data by loan type into loans via credit cards, housing loans, mortgages, etc. We also generated the revenue vs group type graph. This not only helped us visualize the segments with the highest defaulters but also showcased their revenue generation capability.

1. 5) **Interactive map of the United States using Bokeh to showcase the following** :

1. 1)Number of customers by state: The number of customers by state is basically the total number of customers for Lending Club in that state.
2. 2)Percentage of defaulters by state: The percentage of defaulters by state is calculated by dividing the number of defaulters in a state by the total population of that state.

1. 6) **Logistic Regression** :

1. 1)We define dummy variables for the &#39;grade&#39; column - which indicates the riskiness score of the borrower. It is comparable to a FICO score for determining the credit standing of a retail borrower. We set the customer type of &#39;default&#39; as 1 and &#39;not default&#39; as 0 and used the &#39;sm.logit&#39; function to plot the logistic regression.  To decide the parameters to be used for regression, we used the trial and error method and found the variables that are significant in explaining the variation of log odds.
2. 2)From the regression, we computed the coefficients for each variable which can then be tested on the dataset, to find the probability of default in each case. From the regression, we found that all the parameters were significant in explaining the probability of default of each customer.

1. 7) **Calculation of probability of default** :

For this, we begin by adding three columns in our data-frame for the log odds, odds and finally the default probability. Going through the computation of each individually, we finally calculate the default probability for all customers in our dataset.

**Computation Challenges** :

Some of the computation challenges involved were:

1. 1)Data cleaning: This involved converting the string columns of the data frame into numeric type as logistic regression could not be run without data-type conversion. We also had to eliminate all the NA and NaN values from the dataset using &quot;dropna&quot; and the &quot;isfinite&quot; functions.
2. 2)Importing Bokeh: The Bokeh library is large in size and it takes quite a bit of time to import it into the workspace.
3. 3)Running regression: Regression is a complicated process involving a lot of trial-and-error and complicated calculations, which result in time delays during the execution of the code. This is further increases the time taken to process the code.

What is the slowest part of your code and why?

What would happen to the time it takes for your code to run if the size of the data were to double, triple, quadruple, etc.

**Results:**

**Tables and graphs summarizing results**

1. 1)
<img src="https://github.com/sushil1792/LendingClub_loan_default_prediction/blob/master/Defaulters%20vs%20Loan%20Purpose.png"/>                   _Figure 1                                         
<img src="https://github.com/sushil1792/LendingClub_loan_default_prediction/blob/master/Revenue%20Vs%20Loan%20Purpose.png"/>Figure 2_

_                                       _

Through this graph, we can observe that the number of loan defaults were maximum in &quot;Debt consolidation&quot; category. Debt Consolidation essentially means that the purpose of the loan is to re-finance other categories of outstanding loans such as car, credit card, personal loans etc.

Revenue is calculated using the following formula:

Revenue= Lending Amount \* Loan Term (in years) \* Rate of Interest (%)

The maximum revenue is generated from &quot;Debt consolidation&quot; category.

It is interesting to note that the loan categories that have the highest revenue are also those that have the highest defaults.

1. 2)_               
<img src="https://github.com/sushil1792/LendingClub_loan_default_prediction/blob/master/Revenue%20Per%20Loan%20Vs%20loan%20Purpose.png"/> Figure 3_

1. 3)               
<img src="https://github.com/sushil1792/LendingClub_loan_default_prediction/blob/master/Statewise%20No%20of%20Defaulters%20(Bokeh).png"/>  _Figure 4                                               
<img src="https://github.com/sushil1792/LendingClub_loan_default_prediction/blob/master/State%20Wise%20Customers%20(Bokeh).png"/> Figure 5_

Amongst loan categories with respect to purpose of loan, revenue generated per loan is maximum for house purchases followed by loans taken by loans for small businesses. The lowest revenue generated per loan is for vacation purpose        _                                               _

The Bokeh graphs show the State-wise Population, Customer base as well as the Number of Defaulters and Probability of Default.

1. 4)_               
<img src="https://github.com/sushil1792/LendingClub_loan_default_prediction/blob/master/Expected%20Loss%20Vs%20Purpose.png"/>  Figure 6_

1. 5)                                    
<img src="https://github.com/sushil1792/LendingClub_loan_default_prediction/blob/master/Logit%20Regression%20Results.png"/>    _Figure 7_





Amongst loan categories, expected loss is maximum for house purchases followed by loans taken by loans for small businesses. The lowest expected loss per loan is for vacation purpose

**Time Analysis:**

With increase in number of Observation Data, time taken by the &#39;dataread&#39; function increases linearly whereas &#39;Linear Regression&#39; function is very quick to show any variation on the graph.
For the &#39;Logistic Regression&#39; function, with the increase in number of observations, the time graph follows Log(n), whereas with increase in number of independent variables, the time increases linearly.




<img src="https://github.com/sushil1792/LendingClub_loan_default_prediction/blob/master/No%20of%20Observations%20Vs%20Run%20Time%20.png"/> 
<img src="https://github.com/sushil1792/LendingClub_loan_default_prediction/blob/master/No%20of%20Observations%20Vs%20Run%20Time%20-%20Logistic%20Regression%20.png"/> 
<img src="https://github.com/sushil1792/LendingClub_loan_default_prediction/blob/master/No%20of%20Independent%20Variables%20Vs%20Run%20TIme%20-%20Logistic%20Regression.png"/> 
