**Activity_type_project**
--------------------------
**Project description**

Based on smartphone data, we have 21 participants from whose phones the data was taken for the collection being processed. The dataset contains 6 type of activity (target data):

-Walking

-Walking Upstairs

-Walking Downstairs

-Sitting

-Standing

-Laying

For each record in the dataset it is provided:

- Triaxial acceleration from the accelerometer (total acceleration) and the estimated body acceleration.
- Triaxial Angular velocity from the gyroscope.
- A 561-feature vector with time and frequency domain variables.
- Its activity label.
- An identifier of the subject who carried out the experiment.

**The aim of the project is to build a model that predicts the activity being performed as accurately as possible.**

**DATA EXPLORATION AND VISUALIZATION**
--------------------------
Target variable values set is balanced 

![image](https://user-images.githubusercontent.com/96497973/190903588-1e6c9654-816f-4d36-b53d-07063d989bdf.png)

There are big differences between active and static activities for some features

![image](https://user-images.githubusercontent.com/96497973/190903662-1dae19a0-9823-419c-8734-2a70cfafa8d0.png)


The distribution of the different activities

![image](https://user-images.githubusercontent.com/96497973/190903619-9470afaf-e6af-4eb1-93ee-4196e4fb941e.png)

**FEATURE SELECTION** using logistic regression allowed the most useful features to be selected for the model.

Model building was then based on 2 sets of data: all features and those indicated in the logistic regression (125  of 561 features)


MODELS AND RESULTS
--------------------------

**1. K - Nearest Neighbors**

**2. SVM**

**3. Random Forest Classifier**

**RESULTS**

![image](https://user-images.githubusercontent.com/96497973/190904439-4d584478-73df-48b9-9a38-e33874a6ae9f.png)


The models score relatively high and close, according to the above indications the best model would be an SVM trained on the full feature set. 

This model is currently only wrong on 2 static activities - sitting and standing:

![image](https://user-images.githubusercontent.com/96497973/190904529-151b9658-3c6a-42e1-93b8-fea0f2a15fc7.png)

