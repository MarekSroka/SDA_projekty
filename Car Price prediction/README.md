**CAR PRICE PREDICTION**
---------------------------------
**Project description**

The main objective of the project is to predict the car price so it's the machine learning regression problem.

Starter dataset contains the following features:

-Price (target variable)

-Levy -  tax (levy)

-Manufacturer - producer

-Model - model

-Prod. year - year of production

-Category - type of vehicle

-Leather interior 

-Fuel type 

-Engine volume

-Mileage

-Cylinders

-Gear box type

-Drive wheels

-Doors 

-Color 

-Airbags

---------------------------
EDA, data cleaning and visualization
---------------------------
Data processing consisted of:
 
- organising the data and giving them the appropriate data types (e.g. Mileage column)
- removing duplicates and the id column
- due to reducing the number of outliers - downsize the age of cars 
   to 40 yrs., exclusion of luxury cars
- creation of 2 features in the Engine column (capacity and Turbo information)
- removing erroneous rows (e.g. engine capacity = 0)
- use of OrdinalEncoder on categorical features

Checking the correlation between target and features

![image](https://user-images.githubusercontent.com/96497973/190902475-9c43b243-59b5-4366-90dc-1a1464a140c7.png)

![image](https://user-images.githubusercontent.com/96497973/190902379-281a3f07-8724-492b-8b78-ca75d8ac5f03.png)

MODELS AND RESULTS
---------------------------

**1. Linear regression - baseline model**

   RMSE for LinearRegression: 15945.24
   
**2. Decision Tree Regresssor - basic version**

   RMSE for DecisionTreeRegressor:  10607.49
   
**3. Decision Tree Regresssor with the same model, optimal parameters, included categorical data applied as One Hot encoder 
     and log scaler to minimize skewness and transformation of data**
   
   Final RMSE for DecisionTreeRegressor: 10174.0
   
![image](https://user-images.githubusercontent.com/96497973/190902976-70802028-31d5-4917-bf94-cc5d1228221f.png)

![image](https://user-images.githubusercontent.com/96497973/190902984-ca67909f-c733-4500-8689-629ea65baeff.png)

![image](https://user-images.githubusercontent.com/96497973/190902807-cbed1fac-41c9-4b29-8566-bd5e647c0fbd.png)

