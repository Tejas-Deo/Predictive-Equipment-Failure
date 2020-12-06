<h1>PREDICTIVE EQUIPMENT FAILURE</h1>

> Data analysis, Data pre-processing, Machine Learning

Project blog link --> 

This project is about predicting the upcoming failures in machines based on the data pattern using Machine Learning. We have to predict 2 types of failures:-
* 1) Surface Failure (failures occuring on the equipments present on the surface)
* 2) Downhole Failure (failures occuring on the equipments present below the surface/ground which extract the oil from oil wells)

The data that we have is collected from over 107 sensors which store 2 types of information. 
* 1) Measures data (which store a single measurement from the sensor)
* 2) Histogram data (here the data has been recorded from the sensors for 10-time steps)

<b>The "Predictive_equipment_failure_model_productionization.ipynb" file contains the entire Pipeline of my Project. It also has a Flask API built around it as this Project was deployed on the Local System For Testing purposes. The pipeline can handle the errors created by the users while entering the input data and has the capability to show the corresponding error's as well.</b>

<h3>DATA PRE-PROCESSING STEPS</h3>

* 1) Separate the Measures Data and Histogram Data.
* 2) Extract top 29 features from the Measures data (which also includes 4 engineered features).
* 3) Standardize the Measures Data.
* 4) Separate the Measures Data based on the percentage of NAN values and create 3 new Measures Datasets.
* 5) Perform data imputation on all the 3 new Measures datasets (approach for data imputation is discussed in detail in the Project blog link given above).
* 6) After imputation, combine all the 3 datasets and store the Final Measures Data.
* 7) Standardize the Histogram Data and store the Final Histogram Data.
* 8) Combine the Final Measures Data and Final Histogram Data and create a Final Dataset to pass it to the CUSTOM ENSEMBLE MODEL.
* 9) Store all the DATA PRE-PROCESSING MODELS.

<h3>CUSTOM ENSEMBLE MODEL</h3>

<h5>TRAINING OF MODEL (PART 1)</h5>

* 1) Split the Training data into 2 datasets D1 and D2.
* 2) Take D1 and apply random row and column sampling with replacement so as to train 500 Decision Trees as the Base Estimators.
* 3) For each Decision Tree, store the corresponding column names as we require it further.
* 4) The Base Estimators i.e. 500 Decision Trees are trained now. 

<h5>TRAINING OF MODEL (PART 2)</h5>

* 1) Take D2 and perform column sampling based on the column names that we stored in TRAINING PART-1 for each Base Estimator.
* 2) Pass it through the TRAINED BASE ESTIMATORS.
* 3) Create a New Dataset for the Meta Classifier based on the output coming from the trained base estimators.
* 4) Train the Meta Classifier with this new dataset.
* 5) The Meta Classifier is now trained. 

<h5>TESTING OF MODEL</h5>

* 1) Take a test datapoint.
* 2) Sample the data point based on column names stored for the Trained Base Estimators.
* 3) Pass the data point and collect the output from the Trained Base Estimators.
* 4) Create a new corresponding dataset for the Trained Meta Classifier.
* 5) Pass this new dataset through the Trained Meta Classifier and get the output/predicted result

<h3>Access the link given below to see a demo video which describes the working of my Project.</h3>
https://youtu.be/j6eGFZDWw3o 
