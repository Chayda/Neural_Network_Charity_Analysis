# Neural_Network_Charity_Analysis

## Overview:
Analyze data from a csv containing metadata from 34,000+ organizations that have received funding from a fictitious investment firm, using Deep Neural Networks. The goal of the Deep Learning model is to classify the charities that successfully received funding.

**Problem Type:** Classification

**Preprocess data:** Scikit-learn’s OneHotEncoder

**Compile, train, evaluate model:** TensorFlow API

**Optimize model:** objective is to achieve a target predictive accuracy >75%

**Data Source:** charity_data.csv

**Software:** Python version 3.7.6, Jupyter Notebook 6.3.0

## Results:

### Data Preprocessing
-	Target: IS_SUCCESSFUL
-	Features: APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE-CASE, ORGANIZATION, INCOME_AMT, SPECIAL_CONSIDERATIONS
1.	APPLICATION_TYPE and CLASSIFICATION had infrequent values “bucketed” into a category labeled “other”.
2.	All categorical variables were encoded using OneHotEncoder.
-	EIN and NAME were removed from the input data, as they are neither targets nor features.
<img width="305" alt="nn1" src="https://user-images.githubusercontent.com/74624855/140383691-42f8833a-dd64-47ad-a245-7c8a806be278.png">

### Compiling, Training, and Evaluating the Model
-	Initial model was selected to have two hidden layers, with 80 neurons in the first layer and 30 neurons in the second layer – selected by following the general rule of thumb to use 2-3 times the amount of inputs for the number of neurons (44 inputs).
-	The target model performance was not met, with the initial Neural Network resulting in an accuracy of 72% and a loss metric of 0.56, which is pretty high (the goal accuracy was to be >75%). 
-	In an attempt to increase the model performance, the following changes were applied to the initial Neural Network model:
1. ‘Noisy’ variable removed – due to the range of ASK_AMT, the column has been removed;
<img width="290" alt="attempt_1_ask_counts" src="https://user-images.githubusercontent.com/74624855/140383750-ce5ace05-7d0e-4eb0-a6d8-32778985165c.png">
<img width="431" alt="attempt_1_ask_dropped" src="https://user-images.githubusercontent.com/74624855/140383763-c40f4a64-da33-4a7f-aef3-f86e3aac99b0.png">
<img width="308" alt="attempt_1" src="https://user-images.githubusercontent.com/74624855/140383768-e650f1c3-d8d1-4332-b361-5e6733153a23.png">

2. Different model in hidden layer(tanh) with neurons increased to 100 and 50;
<img width="478" alt="attempt_2a" src="https://user-images.githubusercontent.com/74624855/140383832-c19a5bbc-23b9-49ad-9cd0-b4bf7a8f70cf.png">
<img width="500" alt="attempt_2b" src="https://user-images.githubusercontent.com/74624855/140383833-75c3af56-d3b8-47e0-8a54-3c7022c220e9.png">

3. Increased number of hidden layers to three and number of neurons used (80, 30, and 20), and number of epochs increased to 300.
<img width="443" alt="attempt_3a" src="https://user-images.githubusercontent.com/74624855/140383878-682325fb-4c47-4d3f-840e-e003628affa7.png">
<img width="340" alt="attempt_3b" src="https://user-images.githubusercontent.com/74624855/140383886-97b6905e-19e6-45e8-8fab-7f55eb999295.png">

-	In all three attempts to optimize the model, the accuracy remained around 72%, and the loss increased with each attempt; therefore, the optimization of the model was not      successful.
-	Final model saved in a Hierarchical Data Format (HDF5) file. 

## Summary:
As the model was not successful in meeting the target, an alternative to the Deep Neural Netowrk model should be considered. An alternate model should classify a binary outcome, such as Random Forest Classifier (RLC). A RLC would combine multiple decision trees and predict an outcome which could be compared against the performance of the Deep Learning model, with a target accuracy of >75% which was not met using Deep Learning Model.

