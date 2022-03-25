---
title: "PG_Project 4: Credit Risk Modeling"
date: 2022-03-25 20:19:20
permalink: blog/CreditRisk.html
author_profile: true
toc: true
toc_label: "Page Content"

tags:
  - PG Project
  - Financial Analytics
  - Prediction
  - Default Prediction
  - Statistics
  - Classification
header:
  teaser: "/assets/posts/CreditRisk/CRM.jpg"

---

![credit risk](/assets/posts//CreditRisk/CRM.jpg)

## <span style="color:#33a8ff">Introduction</span>

Credit risk modelling refers to the use of financial models to estimate losses a firm might suffer in the event of a borrower’s default. Financial institutions deploy models that draw upon the credit history of borrowers, third-party data – such as rating agency data – and inputs from their own economic stress scenarios to measure credit risk.

## What is Credit Risk Modelling?
There are many different factors that affect a person’s credit risk. This makes assessing a borrower’s credit risk a highly complex task. With so much money riding on our ability to accurately estimate the credit risk of a borrower, credit risk modeling has come into the picture.

Credit risk modelling refers to the process of using data models to find out two important things. The first is the probability of the borrower defaulting on the loan. The second is the impact on the financials of the lender if this default occurs.

Financial institutions rely on credit risk models to determine the credit risk of potential borrowers. They make decisions on whether or not to sanction a loan as well as on the interest rate of the loan based on the credit risk model validation.

As technology has progressed, new ways of modeling credit risk have emerged including credit risk modelling using R and Python. These include using the latest analytics and big data tools to model credit risk. Other factors like the evolution of economies and the subsequent emergence of different types of credit risk have also impacted how credit risk modelling is done.

## Types of Credit Risk Rating Models
Credit risk modeling depends on how effectively you can leverage data about a borrower’s financial history, income, and so on to arrive at an accurate credit score. Big data and analytics are enabling credit risk modelling to become more scientific as it is now based more on past data than guesswork. In fact, credit risk modeling using R, Python, and other programming languages is becoming more mainstream. Here’s an excellent video which discusses different credit risk rating models.

Here are the three major types of credit risk rating models that are used to determine credit risk.

### (i) The Models Based on Financial Statement Analysis
Examples of these models include Altman Z score and Moody’s Risk Calc. These models are based on an analysis of financial statements of borrowing institutions. They chiefly take into account well known financial ratios that can be useful in determining credit risk. For instance, Altman Z score takes into account financial ratios like EBIDTA/total taxes and sales/total assets in different proportions to determine the likelihood of a company going bankrupt.
### (ii) The Models Measuring Default Probability
The best example of this kind of credit risk modeling is structural models like the Merton model. Structural models consider business failures to be an endogenous event which depends on the capital structure of the company. In other words, they operate on the assumption that a business will fail and default on its loans if its value falls below a certain threshold.

### (iii) Machine Learning Models
The introduction of machine learning and big data to credit risk modeling has made it possible to create credit risk models that are far more scientific and accurate. A great example of this is the Maximum Expected Utility model which is based on machine learning.

## Data and modeling
In this project,  you are given a [dataset](https://www.kaggle.com/competitions/credit-risk-modeling-case-study/data) which is consisting of over 111,000 loan records, you must
1. explore and clean the dataset
2. find the best way to determine the best way to predict whether a loan applicant will fully repay or default on a loan.
3. You must then build a machine learning model that returns the unique loan ID and a loan status label that indicates whether the loan will be fully paid or charged off.

The dataset consists of the following fields:
- Loan ID: A unique Identifier for the loan information.
- Customer ID: A unique identifier for the customer. Customers may have more than one loan.
- Loan Status: A categorical variable indicating if the loan was paid back or defaulted.
- Current Loan Amount: This is the loan amount that was either completely paid off, or the amount that was defaulted.
- Term: A categorical variable indicating if it is a short term or long term loan.
- Credit Score: A value between 0 and 800 indicating the riskiness of the borrower’s credit history.
- Years in current job: A categorical variable indicating how many years the customer has been in their current job.
- Home Ownership: Categorical variable indicating home ownership. Values are "Rent", "Home Mortgage", and "Own". If the value is OWN, then the customer is a home owner with no mortgage.
- Annual Income: The customer's annual income
- Purpose: A description of the purpose of the loan.
- Monthly Debt: The customer's monthly payment for their existing loans
- Years of Credit History: The years since the first entry in the customer’s credit history
- Months since last delinquent: Months since the last loan delinquent payment
- Number of Open Accounts: The total number of open credit cards
- Number of Credit Problems: The number of credit problems in the customer records.
- Current Credit Balance: The current total debt for the customer
- Maximum Open Credit: The maximum credit limit for all credit sources.
- Bankruptcies: The number of bankruptcies
- Tax Liens: The number of tax liens.

## Conclusion
You need to present a credit evaluation of your model.

## <span style="color:#33a8ff">References</span>
- [Sample code](https://www.kaggle.com/code/yashmd/dimensionless-coding-round-1-yash-mahadeshwar).
- [credit risk modelling](https://www.listendata.com/2019/08/credit-risk-modelling.html)
- [A Beginner’s Guide to Credit Risk Modelling](https://www.digitalvidya.com/blog/credit-risk-modelling/)
- [Credit Risk Modeling in Python](https://www.datacamp.com/courses/credit-risk-modeling-in-python)

<p>
{% include  share.html %}
</p>

<span style="color:#9e9696"><i> Last updated: 25/03/2020</i> </span>

<p>
{% include  license.html %}
</p>