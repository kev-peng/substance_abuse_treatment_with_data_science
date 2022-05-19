# Table of Contents

- [Files](#Files)
- [Executive Summary](#Executive-Summary)
- [Methodology](#Methodology)
- [Data Dictionary](#Data-Dictionary)
- [Evaluation](#Evaluation)
- [Findings and Recommendations](#Findings-and-Recommendations)
- [Next Steps](#Next-Steps)
- [Citations](#Citations)

# Files

Run in sequence  

01dataprep - Used to create lookup tables and SQLite Database  
02edamodeling - For EDA, modeling and evalualtion

# Executive Summary

Over the recent decade, there has been a growing concern over the abuse of substances and overdose deaths. Treating substance abuse is imperative for a person’s road to recovery. However, there are limited resources and no two patient’s are the same. This presents a challenge as there are different factors that can be attributed to a patient completing treatment or not. With available data from SAMSHA (Substance Abuse and Mental Health Services Administration), the task was to create a predictive model with various features to predict whether or not a patient will complete treatment or not. The goal is to reduce false positives so that patients would prematurely be discharged from treatment. Tree based models tend to do the best and the model with the best precision score is the Random Forest with no hyperparameter tuning with a precision score of .69.

# Problem Statement

Kevin Peng was hired by the ASAC (Association of Substance Abuse Clinicians) IPA to construct a model to help their members make predictions on whether or not a patient will complete treatment. The goal is to use the model to help with data-driven decision-making and resource allocation.

# Methodology
1. Gather the initial data
2. Performed EDA
3. Preprocess Data
4. Create models
5. Hypertune best performing models
6. Evaluate models/pickle models

# Data Dictionary

|Feature|Type|Description|
|---|---|---|
|**education**|*obj*|Patient’s education level| 
|**marital_status**|*obj*|Patient’s marital status|
|**service**|*obj*|Treatment service|
|**len_stay**|*obj*|Number of days a patient stayed at a program prior to exiting treatment. Calculated using the date of admission and the last date of contact|
|**ref_source**|*obj*|Referral source for patient to receive service(s)| 
|**treatm_ep**|*obj*|Whether or not a patient has recieved treatment in the past| 
|**num_arrest**|*obj*|The number of times a patient was arrested 30 days prior to treatment| 
|**empl_status**|*obj*|Patient’s employment status at the time of service|
|**gender**|*obj*|The sex of patient|
|**housing**|*obj*|Housing status of patient|
|**diagnosis**|*obj*|Diagnosis based on DSM criteria| 
|**age_range**|*obj*|Age category of patient| 
|**p_income**|*obj*|Patient’s primary source of Income| 
|**substance_1**|*obj*|Patient’s primary substance of choice| 
|**afu**|*obj*|Patient’s age of first use of substance identified|
|**self_attend**|*obj*|Frequency of attendance for self-help 30 days prior to admission|
|**reason**|*obj*|Reason for exiting service|

# Evaluation

The goal is to reduce false positives as the cost for predicting a patient as completing treatment prematurely can be life and death. This has the potential of a patient relapsing and overdosing if they were truly not ready to exit treatment.

|Model|Training Accuracy Score|Testing Accuracy Score|Precision Score|
|---|---|---|---|
|**Logistic Regression Basic**|*0.700465452*|*0.699171679*|*0.594866005*| 
|**Random Forest Basic**|*0.981186381*|*0.691109759*|*0.602481361*|
|**Decision Tree Basic**|*0.981180892*|*0.748134141*|*0.685835466*|
|**Bernoulli NB Basic**|*0.649174481*|*0.659126114*|*0.556876222*|
|**KNN Basic**|*0.823103544*|*0.686812247*|*0.584299827*|
|**Random Forest Hyper 1**|*0.831231801*|*0.748058702*|*0.663909016*|
|**Random Forest Hyper 2**|*0.818545764*|*0.745126637*|*0.65679285*|
|**Random Forest Hyper 3**|*0.893571768*|*0.757601742*|*0.684022325*|
|**Xgboost Hyper 1**|*0.764277795*|*0.745471142*|*0.652793872*|
|**Xgboost Hyper 2**|*0.818545764*|*0.745126637*|*0.65679285*|
|**Xgboost Hyper 3**|*0.925814472*|*0.752700718*|*0.67836139*|

# Findings and Recommendations

The features with the largest coefficients belongs primarily to the category of len_stay. Recommendations on the best way to incorporate the model for treatment are:

- Use the model as a tool for treatment planning/case conferencing alongside with assessment tools and patient own goals

- Try to reengage patients into treatment if they stop showing up or prematurely terminate service

- Feed updated information for better predictions as data the time of admission might be different at discharge

# Next Steps

More Data

- 2018 and prior data
- Retrain Model
- Use for validation
- Test Performance of the model on new data
- Frequency of sessions as a feature
    - Individual Counseling
    - Group Counseling
- Overall time spent with a patient as a feature

Tailor Models

- Create models for different service types
    - Compare the performance of those models
- Multiclass classification

Preprocessing

- SMOTING or avoid using oversampling

Further Feature Engineering/Extraction

- Experiment with categorical datatypes
- See if there is a change in model performance
- Combine Features together
    - Example: Substance 1 + 2 + 3
- PCA

# Citations

https://www.cdc.gov/nchs/nvss/vsrr/drug-overdose-data.htm  
https://nymag.com/intelligencer/2021/03/deaths-of-despair-have-surged-among-people-of-color.html  
https://www.kaggle.com/code/hamelg/python-for-data-25-chi-squared-tests/notebook  
https://machinelearningmastery.com/feature-selection-with-categorical-data/  
https://github.com/scikit-learn/scikit-learn/discussions/20690  
https://stackoverflow.com/questions/61325314/how-to-change-plot-confusion-matrix-default-figure-size-in-sklearn-metrics-packa  
https://stackoverflow.com/questions/53574918/how-to-get-rid-of-white-lines-in-confusion-matrix  
https://stackoverflow.com/questions/67294768/how-can-i-change-the-font-size-in-this-confusion-matrix  
https://towardsdatascience.com/beginners-guide-to-xgboost-for-classification-problems-50f75aac5390  
https://www.youtube.com/watch?v=ap2SS0-XPcE&t=987s&ab_channel=HarshKumar  
https://towardsdatascience.com/xgboost-fine-tune-and-optimize-your-model-23d996fab663  
https://www.datafiles.samhsa.gov/dataset/teds-d-2019-ds0001-teds-d-2019-ds0001  



=======
# Substance-Abuse-Treatment-with-Data-Science
>>>>>>> ef8700a0e1fd7f209a8a153bfbd276be682e6b08
