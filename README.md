
**Prediction of debt repayments as an important part of the debt portfolio valuation process**

----------------------------------------------------------------------------------------------------------------------------------------------------------------
**Agenda**

Project description and objective

Data collection and pre-processing

Data Engineering with visualizations

Modelling and evaluation

Conclusions and possibility of extending the model

-----------------------------------------------------

**Project Objective**

   - Prediction of repayment status („paying”) in debt collection cases
   - Binary classification problem

 --------------------------------------
 
**Data Collection**

The data to build the dataset was selected from the database of a debt collection company

The dataset was mostly prepared before the project started 

Data selection criterion:

 - active cases with the debt collector
 
 - portfolios purchased since 2015
 
 - data from the entire cross-section of the company's operations, mainly banking entities and loan companies

------------------------------------
 
 **Data Collection problems**
 
- Missing data

- Inconsistent data (e.g. dates and categorical values)

- Outliers

- Differences between historical data and current data attached to valuation by business partners

-------------------------------------

**Data and feature Engineering**

Input dataset had 12 features and explanatory variable (target)

- 3 categorical variables
- 9 numeric variables
- About 111k rows

![image](https://user-images.githubusercontent.com/96497973/177940481-407ea50e-bb82-488c-bf83-125da1b7c32d.png)


Data cleaning consisted of:
- removal of obvious errors in the data (value of debt less than 0)
- completing Nan values in 3 columns

- **8 new features** were created from the existing data

The 5 features that formed the basis for the new columns were removed and the final dataset looked like the one in the graphic


![image](https://user-images.githubusercontent.com/96497973/177941204-222fbd37-9d10-4b16-9061-f8e0982ead3d.png)

-------------------------------------

**Data visualization**

- Numerical ratio features on a box plot:

![image](https://user-images.githubusercontent.com/96497973/177941910-06a3d368-4580-43a0-ba75-0111a9ebbbc2.png)


- Age in relation to repayment status

![image](https://user-images.githubusercontent.com/96497973/177942331-156153fe-8cac-4a85-86f4-c795ad331a99.png)    ![image](https://user-images.githubusercontent.com/96497973/177942319-70ae0253-12b6-4249-bc17-1a7a7f4f1544.png)

- Days past due in relations to  repayment status

![image](https://user-images.githubusercontent.com/96497973/177942453-03c53d99-fc25-4151-bf13-fb18a4aa14a5.png)

- Correlation matrix 

![image](https://user-images.githubusercontent.com/96497973/177942535-e5737a3b-0512-4ea9-a152-4921a87f6bff.png)

High correlation in feature pairs:

- time on book and liczba dni od daty umowy

- ratio_sop_to_debt and  ratio_credit_to_debt

- liczba_dni_od_daty_umowy and liczba_dni_od_daty_wypowiedzenia

- dpd and time_debt_exist

The conclusion for further processing is to keep all features (the collection does not have many) and not to use dimensionality reduction (so as not to lose interpretability)

---------------------------------------

**Measurement correlation between variables and target**

Measurement correlation between numeric variables and target.

If we set the cut-off point at 0.15, apart from the variables wiek and ratio_capital_to_debt the rest are not correlated with the target.

P-value tells us if the result of an experiment is statistically significant in all cases (value < 0.05).


Identifying the influence of categorical values to target by checking mean value for each categorical:


![image](https://user-images.githubusercontent.com/96497973/177951341-0f0f2fa9-16bb-4ab9-ac11-896efb9fc969.png)

![image](https://user-images.githubusercontent.com/96497973/177951366-4eb700cc-86aa-410c-b6e5-98a414edb235.png)

![image](https://user-images.githubusercontent.com/96497973/177951376-5d60b047-c195-4730-9f66-8dcfe38e3321.png)



- Spliting dataset into training(100591) and testing(11177) subsets

- Baseline model is predicting the most common class of the outcome variable for all observations    
    -->  all cases in dataset would be 'paying’ (distribution 0.53 to 0.47)

3 models were selected for training:

- Decision Tree Classifier
- Random Forest Classifier
- XGBoost Classifier

Training  models in pipelines with assumptions:

- use One-Hot Encoding on categorical variable

- use of Chi-Square (with SelectPercentile) test for feature selection

- HalvingGridSearchCV for CV = 10, scoring = f1 macro

- Tuning a group of hiperparameters before the learning process


- Decision Tree Classifier

![image](https://user-images.githubusercontent.com/96497973/177964084-159d04e9-9ae4-4ced-8100-b224c9d32306.png)

- Random Forest Classifier

![image](https://user-images.githubusercontent.com/96497973/177964219-2505e022-b3d5-49f2-816b-50b9000d26a4.png)

      
 - Boost Classifier
      
  ![image](https://user-images.githubusercontent.com/96497973/177963662-36c8fbab-7380-4d74-ac2d-b2381bc21060.png)   


--------------------------------------------------
**EVALUATION**

**Final results of models:**

![image](https://user-images.githubusercontent.com/96497973/177973428-c3a59154-01f3-45ef-bd82-8e842fc20b2e.png)

- All models scored higher than the baseline model	
- Random Forest Classifier and XGBoost got almost the same final score = 75% of F1 score and 75% of Accuracy

- Best hyperparameters for Random Forest Classifier:
      chi2_percentile: 80, criterion: 'gini’, max_depth: 22, min_samples_leaf: 6, 
      min_samples_split: 10, n_estimators: 1400	
      
  
-----------------------------------------------------
**SHapley Additive exPlanations**

The features most influencing the results of this model were:
 - the conduct of external debt collection
 - the number of days since agreement
 - the number of days since termination
 - the ratio of the sum of payments to the amount of the debt
 - the ratio credit to debt

![image](https://user-images.githubusercontent.com/96497973/177973721-b357bd78-1589-42af-ab98-ab257461f7d9.png)

On Random Forest Classifier model

--------------------------------------------------------------

**BUSINESS ENVIRONMENT**

Prediction were made on 3 intuitively created cases


Chosen model made predictions on inupt data:

 - case_01 and case_03 would be 'paying’ (value ‚1’)
 
 - case_02 would be  ‚not paying’ (value ‚0’)

--------------------------------------------------------------------------------
**CONCLUSIONS AND FURTHER STEPS**


The results obtained so far have shown that the project has the potential to correctly predict the problem and can certainly be improved.

Next steps:

- thorough analysis of company data with a view to selecting the optimal set

- monitoring incoming data to collect a larger and more a larger and more valuable sample for the study

- the project may go in the direction of predicting the probability of repayment , then on this basis coefficients may be defined to identify the predicted repayment      curves 


