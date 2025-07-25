# dataprojects

The model classifies patients probability to be readmitted to the hospital based on the amount of outpatient visits in the year preceding the encounter.
This project aims to use a machine learning model to predict hospital readmission. I utilized publicily available datasets from the UC Irvine Machine Learning Repository. This particular dataset represents diabetes care for ten years between 1999-2008 across 140 hospitals and has over 100,000 datapoints.
Link to the data: https://archive.ics.uci.edu/dataset/296/diabetes+130-us+hospitals+for+years+1999-2008. It looked for early readmission of patients within 30 days of discharge. In terms of binary comparisons, we are looking for whether a patient is likely to be readmitted.

### Readmission 
I began by reading in historical data related to readmission. I created a new column for binary readmission (0 for no readmission, 1 for readmission). I classified the <30 day readmission and >30 readmission both into the same category of 1, which is simply that the patient was readmitted.

Plotting the readmission risk was first done by looking at the mean of readmission to see how often it occured, which was with 46% of patients. Based on this plot, we can deduce that more outpatient visits could be a predictor of readmission.

### Linear Regression
To test the impression of outpatient visits being a predictor of readmission, this impression by I needed to perform a linear regression on the data. The result can be interpreted by if a patient has 10 outpatient visits, there is about a 75% chance they will be readmitted. This type of linear probability model is useful for when we are looking for the probability of something that is hard to predict. We can also infer that the amount of outpatient visits is positively correlated with the likelihood of readmission. To have an exact predicted readmission risk for each patient, I created a column called predicted.

### Prediction for the future
To test this model, I created future patients by generating randomized amount of outpatient visits for 100,000 patients. I assigned them a random amount of outpatient visits between 0 and 42, since 42 was the highest number of outpatient visits recorded in the past.
I then used the regressor I previously fit to make attrition predictions for a new datset. From printing out the head, we can see that the pattern of readmission with a high number of outpatient visits matches the past pattern because these predicted probabilities were generated using the regressor trained on the past dataset.

The final bit of code predicts those with the highest to lowest prediction of readmission based on the results of the logistic regression. This logistic regression is used to predict the binary outcome of whether or not a patient is readmitted. 
