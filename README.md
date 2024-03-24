# Real-Estate-Price-Prediction
## Overview
This project focuses on predicting real estate prices using a linear regression model. It's designed to demonstrate the application of data preprocessing, model building, and evaluation techniques in Python.
## Installation

To run this project, ensure you have Python installed on your system. You will need the following packages:

-   numpy
-   pandas
-   sklearn
-   statsmodels


## Usage

The notebook is divided into several steps, each illustrating a specific part of the machine learning workflow:
### Step 1: Import the required packages

This step involves importing necessary Python libraries such as numpy, pandas, sklearn, and statsmodels.

### Step 2: Prepare the Data & Data Preprocessing

-   Data is loaded from a CSV file named 'Real estate.csv'.
-   The transaction date variable is obviously not a usable variable in a linear regression and could perhaps be used in conjunction with the house built date variable if it were available. However, in the data preprocessing stage, we considered deleting the variable straight away.
-   Null values in each column are checked and handled accordingly.

### Step 3: Building the Linear Model

-   A linear regression model is built using sklearn and statsmodels to predict real estate prices based on the processed data.

## Model Interpretation
### Model 1
-  X2 house age
-  X3 distance to the nearest MRT station
-  X4 number of convenience stores
-  X5 latitude
-  X6 longitude
-  Y house price of unit area

Model 1 evaluation: 
|variable           |coefficient value        |t value                      |p value                       |
|----------------|-------------- |-----------------|-----------------------------|
|const|-5550.4112|-0.756|0.450
|X2|-0.2851|-6.284|0.000
|X3|-0.0040|-4.742|0.000
|X4|1.1958|5.384|0.000
|X5|261.2912|5.077|0.000
|X6|-7.6623|-0.131|0.896

**MSE**
|Dataset          |MSE value                            |
|----------------|------------------------------------------------------------|
|train set|83.7528
|test set|61.5303


**F value=84.64**  
 **p value=0.000** 
 
Given alpha = 0.05, we can find that the constant coefficients as well as the X6 variable in the first model are not significant and the rest of the variables are significant. According to the F-test, the model is significant overall.
Since the X6 variable was not significant, consider dropping it to rebuild the model 2.

### Model 2
-  X2 house age
-  X3 distance to the nearest MRT station
-  X4 number of convenience stores
-  X5 latitude
-  Y house price of unit area

Model 2 evaluation: 
|variable           |coefficient value        |t value                      |p value                       |
|----------------|-------------- |-----------------|-----------------------------|
|const|-6499.5254|-5.093|0.000
|X2|-0.2847|-6.295|0.000
|X3|-0.0039|-6.910|0.000
|X4|1.1976|5.411|0.000
|X5|262.0035|5.127|0.000

**MSE**
|Dataset          |MSE value                            |
|----------------|------------------------------------------------------------|
|train set|83.7572
|test set|61.5322

**F value=106.1**  
 **p value=0.000** 
 
Given alpha = 0.05, we can find that the intercept term as well as all variables in the second model are significant. According to the F-test, the model is significant overall.
Although all the variables are significant in model 2, excluding only X6 longitude is not reasonable enough for the interpretation of the model, so consider excluding X6 longitude and X5 latitude for model 3.

### Model 3
-  X2 house age
-  X3 distance to the nearest MRT station
-  X4 number of convenience stores
-  Y house price of unit area

Model 3 evaluation: 
|variable           |coefficient value        |t value                      |p value                       |
|----------------|-------------- |-----------------|-----------------------------|
|const|43.0276|26.199|0.000
|X2|-0.2729|-5.819|0.000
|X3|-0.0053|-10.053|0.000
|X4|1.3494|5.927|0.000

**MSE**
|Dataset          |MSE value                            |
|----------------|------------------------------------------------------------|
|train set|90.5112
|test set|62.1394

**F value=123.2**  
 **p value=0.000** 
 
Given alpha = 0.05, we can find that the intercept term as well as all variables in the second model are significant. According to the F-test, the model is significant overall.

## Conclusion
There is some difference between the MSEs of Model 2 and Model 3 on the training set, but the difference on the test set is not significant. Model 3 has a more reasonable variable selection compared to model 2.
