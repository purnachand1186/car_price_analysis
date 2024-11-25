# Used Car sales & Price Analysis
An Analysis on used cars to predict the key factors impacting the price of an used car using ML &amp; AI Model

**Use 'prompt_II.ipynb'**

![DealerImage](images/kurt.jpeg)

## Overview

This is analysis , I used a vehicle dataset provided by Berkeley ML team (also avaialable in kaggle),  the original dataset has around 1 million records, but due to computational resource limitation, I used samples of 20K. The primary goal is to understand data, clean the data, understand the patterns in data , use ML models and find out which model predicts the car prices close to real.

This github has two jupyter notebook files, I am using '**prompt_II_ver2.ipynb**' for my learning purpose, always refer to **prompt_II.ipynb** for the correct anlysis

# Methodology used 

The CRISP-DM (CRoss Industry Standard  Process  for  Data  Mining)  project addressed  parts  of these  problems  by  defining  a  process  model  which  provides  a  framework  for  carrying  out  data mining  projects  which  is  independent  of  both  the  industry  sector  and  the  technology  used.  The
CRISP-DM  process  model  aims  to  make  large  data  mining  projects,  less  costly,  more  reliable,
more repeatable, more manageable, and faster.

![DealerImage](images/crisp.png)

# Business Objective: 

Identify the key factors that influence used car prices ,and below are some of the key business aspects.

Cost: estimate the price of a used car based on the attributes provided for cars in the dataset more precisely try to answer the below business questions 1) Is the price of a car dependent on the milage driven ? 2) Is the price of a car dependent on the engine type and /or horsepower ?
Customers: Understand what customers are looking for in the used cars to provide them with the best options, to acheive that , analyze the exsting customer data to define the patterns depanding on the income, age, status and education.
Data: Make sure the provided for this analysis is in a shape to use it for the analysis and for future predictions. Make sure the outliers are removed.

# Data Understanding 

In the inpout data, there are many null values exists across all columns

<img width="125" alt="image" src="https://github.com/user-attachments/assets/f456eb95-b6c0-4bc0-919f-a045b654a07c">

and there are few outliers in price and year columns

<img width="198" alt="image" src="https://github.com/user-attachments/assets/525a0dfc-6193-44ea-9d98-d7e5c5241d23">

After applying the correlation on the initial data, it is evident that price and odometer has positive correlation

<img width="408" alt="image" src="https://github.com/user-attachments/assets/6d6e3d4d-79a5-4399-a9ec-0a0becade04d">

# Data Prepation
1. Drop null value rows
2. Choose only those records where price and odometer column values are greater than 0
3. Delete duplicate records
4. deleted unnecessary columns ID, VIN & Size

After performing the above steps, the data is now clean with no null values

<img width="265" alt="image" src="https://github.com/user-attachments/assets/1c1bdef8-6d11-461e-9ef0-0250ce18e709">

5. Removed outliers using IQR

<img width="392" alt="image" src="https://github.com/user-attachments/assets/955808d6-e8f5-4556-8eb5-1fe371c5d3ee">

<img width="397" alt="image" src="https://github.com/user-attachments/assets/3bcce046-9c2a-470c-95ce-15efc58a458b">

After remving the outliers, we only got the cars data beginning 1975 till 2022

Before Executing ML models, I converted the categorical column values to integerby using Label Encoder

Since now every column is either integer or float , I used heat matrix to find out relationships.

<img width="587" alt="image" src="https://github.com/user-attachments/assets/434193e2-be90-453f-a08c-bccd2c9e32cf">

from the above matrix here are some of the observations

1.As expected price and Year has positive correlation
2.Price and number of cylinders has postive correlation
3.Surprisngly paint color also has positive correlation with price, type and drive types
4.year has negative correlation with odometer and surprisngly with fule type
5.Cylinders and fuel has negative correlation

# Data Model

Used Below ML models on the cleaned data to find out which model predicts the price value on the development data

1. Simple Linear Regression
2. Linear Regression with Polynomial Features with Degree 2
3. Linear Regression with Grid Search
4. Ridge Regression with Grid Search
5. Lasso Regression with Grid Search
6. Sequnetial feature selection
8. K-Fold Feature selection

and, here are the results

<img width="390" alt="image" src="https://github.com/user-attachments/assets/eb8c71f1-0688-4218-8a9f-9709639037cf">

In my case, Lasso regression returned best MSE & MAE values along with best Accuracy values

<img width="381" alt="image" src="https://github.com/user-attachments/assets/5b5ee790-f44d-4cb0-8618-56cf5780cd5c">

Used Permutation Importance on top of the Lasso Regression model to find out the feature importance

<img width="385" alt="image" src="https://github.com/user-attachments/assets/12154a79-5c40-422e-b4af-b540a7cb3986">

# Observations

1. In recent years (2010-2023) there is a spike in the hybrid / Electric cars category
   
<img width="400" alt="image" src="https://github.com/user-attachments/assets/7a15ab0d-a6c4-4f26-8477-424b3bdb4aa5">

3. Ford F-150 is the best selling car in between 2010-2022 and Chevy Silverado is the second best seeling car
   
<img width="147" alt="image" src="https://github.com/user-attachments/assets/4e0e2e5f-d00b-4d71-9f20-1dbd1d0ab7cf">

These are the top features customers are looking for

1. Year
2. transmission
3. cylinders
4. drive
5. odometer

The dealership should keep Silverado 1500 and Ford F-250 models in their inventory considering the trends and cosnidering the recent trends it is ideal to keep electric and hybrid vehicles with better milage in the inventory






