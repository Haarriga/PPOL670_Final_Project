# PPOL670 Final Project
## Ming & Huixin

Repository: https://github.com/Haarriga/PPOL670_Final_Project.git

Pages: https://haarriga.github.io/PPOL670_Final_Project/

# Data Analysis Project
The objective of this project is to demonstrate an analysis relevant to labor force participation using the tools learned in this course. We would like to build the predictive model to predict individual's labor status (whether the individual is in labor force) and contribute to the development of supporting programs to provide job training and economic support programs for the individuals out of labor force. 

## Data chosen 
The data sets we find are Annual Social and Economic (ASEC) Supplement. It provides the usual monthly labor force data, but in addition, provides supplemental data on work experience, income, non-cash benefits, and migration. Comprehensive work experience information is given on the employment status, occupation, and industry of persons 15 years old and over.
We can access the data through web APIs as the data dictionary linked https://www2.census.gov/programs-surveys/cps/techdocs/cpsmar22.pdf.

## Variable Inclusion and Definition 
### Dependent Variable: Binary variable - labor status
Our primary dependent variable is in_labor, which is re-coded based on A_EXPLF, with values of 0 and 1. If the individual is in labor force, in_labor equals 1, otherwise it equals 0.

In this case, we define whether the individual is in labor force by the following criteria. 
**Labor force **
Persons are classified as in the labor force if they are employed, unemployed, or in the Armed Forces during the survey week. The "civilian labor force" includes all civilians classified as employed or unemployed. The data set includes labor force data for civilians age 15 and over. 

**Not in labor force**
Included in this group are all persons in the civilian non-institutional population who are neither employed nor unemployed. Information is collected on individual's desire for and availability to take a job at the time of the CPS interview, job search activity in the prior year, and reason for not looking in the 4-week period prior to the survey week. This group includes discouraged workers, defined as persons not in the labor force who want and are available for a job and who have looked for work sometime in the past 12 months (or since the end of their last job if they held one within the past 12 months), but who are not currently looking because they believe there are no jobs available or there are none for which they would qualify.

### Predictors: Supplemental Poverty Measure (SPM)
The supplemental poverty measure (SPM) is a measure of economic deprivation. It defines poverty status for families and individuals by comparing resources against a measure of need. Measures of need are used to establish poverty thresholds that are valued in dollars.

We include child care and work expenses, medical out-of-pocket expenses, number of kids in the family, Child Tax Credit, internet subsidy, family type, housing subsidy, child support paid, Federal Earned Income Tax Credit, Federal Tax,  geographic food, shelter, clothing and utility (FSCU) adjustment, and energy subsidy in the SPM sections as our predictors in the models.

### Predictor: Income 
For each person in the sample who is 15 years old and over, questions are asked on the amount of money income received in the preceding calendar year from each of the following sources: (1) money wages or salary; (2) net income from non-farm self-employment; (3) net income from farm self- employment; (4) Social Security or railroad retirement; (5) Supplemental Security Income; (6) public assistance or welfare payments; (7) interest (on savings or bonds); (8) dividends, income from estates or trusts, or net rental income; (9) veterans' payment or unemployment and  compensation; (10) private pensions or government employee pensions; (11) alimony or child support, regular contributions from persons not living in the household, and other periodic income.

We include federal gross income,Earned income tax credit, the annual amount of child support paid, the amount of public assistance or welfare received last year, interest income, total persons income, whether the individual received any dividend last year, total earnings, and total amount of disability income received last year. 

### Predictor: Region 
The numeric variable, census region, are included in the model as a predictor, ranging from 0 to 5. 
Values: (1) 0 = not in universe (under 1 year old); (2) 1 = northeast; (3) 2 = mid west; (4) 3 = south; (5) 4 = west; (6) 5 = abroad. 

### Predictor: Educational Attainment 
Educational attainment is coded as a numeric variable, ranging from 31 to 46. 

### Predictor: Marital Status 
Marital status is coded as a numeric variable, ranging from 1 to 7. 
Values: (1) = Married - civilian spouse present; (2) 2 = Married - AF spouse present; (3) 3 = Married - spouse absent (exc.separated); (4) 4 = Widowed; (5) 5 = Divorced; (6) 6 = Separated; (7) 7 = Never married. 

### Predictor: Health Status
Health status is coded as a numeric variable, ranging from 1 to 5. 
Values:(1) 1= Excellent; (2) 2= Very good; (3) 3= Good; (4) 4= Fair; (5) 5= Poor. 

### Predictor: Race 
Individual's race is coded as a numeric variable, ranging from 1 to 26. 
Values: 01 = White only; 02 = Black only; 03 = American Indian, Alaskan Native only (AI); 04 = Asian only; 05 = Hawaiian/Pacific Islander only (HP); 06 = White-Black; 07 = White-AI; 08 = White-Asian; 09 = White-HP; 10 = Black-AI; 11 = Black-Asian; 12 = Black-HP; 13 = AI-Asian; 14 = AI-HP; 15 = Asian-HP; 16 = White-Black-AI; 17 = White-Black-Asian; 18 = White-Black-HP; 19 = White-AI-Asian; 20 = White-AI-HP; 21 = White-Asian-HP; 22 = Black-AI-Asian; 23 = White-Black-AI-Asian; 24 = White-AI-Asian-HP; 25 = Other 3 race comb; 26 = Other 4 or 5 race comb. 

### Predictor: Medical expenses
We include Out of pocket expenditures for non-premium medical care as the indicator for medical expenses. 

### Predictor: Medical Insurance Coverage 
We include the binaries variables for Medical Insurance, including whether the individual had Medicaid coverage last year, whether the individual have Medicaid coverage this year, whether the individual had market coverage last year, whether the individual have market coverage this year, whether the individual had any current direct-purchase coverage last year, and whether the individual have any current direct-purchase coverage this year. 

### Predictor: Disability and Health Status
We include the categorical variables for individual's disability (whether the individual has a health problem or a disability which prevents work), whether some in the family retired or left a job for health reasons, and whether the individual received any income as a result of health problems. 
Values: (1) 0 = niu; (2) 1 = yes; (3) 2 = no. 

### Predictor: The length of lay-off from work 
We include the numeric variable for the length of looking for work or on layoff from a job, ranging from 0 to 51 (unit: week). 

### Predictor: Age 
The individual's age is coded as categorical variable, ranging from 0 to 17. 
Values: 0 = Not in universe; 1 = 15 years; 2 = 16 and 17 years; 3 = 18 and 19 years; 4 = 20 and 21 years; 5 = 22 to 24 years; 6 = 25 to 29 years; 7 = 30 to 34 years; 8 = 35 to 39 years; 9 = 40 to 44 years; 10 = 45 to 49 years; 11 = 50 to 54 years; 12 = 55 to 59 years; 13 = 60 to 61 years; 14 = 62 to 64 years; 15 = 65 to 69 years; 16 = 70 to 74 years; 17 = 75 years and over. 

### Predictor: Sex 
The individual's sex is coded as a binary, with the value of 1 representing male and 2 representing female. 

# Methods (choose one or more)
The tools we choose to meaningfully inform the policy debate around the issue are supervised machine learning.
## Supervised machine learning
We aim to use individuals' demographic characteristics (e.g. gender, age, education, marital status, etc.)and basic economic characteristics (e.g. SNAP benefits, EITC receipts, etc.) to predict individual's labor status.
We first performed supervised machine learning without PCA. The four models we trained were logistic model, LASSO model, Decision Tree and Random Forest. As logistic model performed significantly worse compared to LASSO model, we did not include it in the later modeling with PCA. The Random Forest model performed the best in both accuracy and sensitivity despite the fact that we generated relatively few trees.

## Principal Component Analysis 
After conducting explanatory analysis, we found that some predictors in the data are correlated. To reduce the number of variables and multicollinearity in a data set while maintain the statistical properties of the data, we utilize Principal Component Analysis to transform potentially linearly correlated variables into a set of linearly uncorrelated variables and apply supervised machine learning in the reshaped data set. 
