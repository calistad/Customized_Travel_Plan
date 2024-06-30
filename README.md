# Customized_Travel_Plan

## Overview

Create an customized efficient travel plan for clients in 4 aspects.

* Present 600+ **cities**, nearby **airports**, **hotels**, and **restaurants** with clients’ preferable weather.
    
* Predict whether the clients’ selected flights from 18 Airlines will be delayed.

* Suggest the most suitable **Airbnb** to clients based on selected features.

* Propose housing **price** estimation on clients' desirable Airbnb.

## 1. Find the Preferable City

### Approach

Retrieve the weather of 1000+ cities in the US using Weather API.

![Screen Shot 2022-09-18 at 6 19 13 PM](https://user-images.githubusercontent.com/88747464/190930360-732ab56c-ad16-4d50-87ee-137f3da49ccd.png)

Present nearby places using Google API.

![Screen Shot 2022-09-18 at 6 20 48 PM](https://user-images.githubusercontent.com/88747464/190930364-4e20ea48-f671-4488-8d2a-fbe5df8ce485.png)

Clients choose preferable weather.

![Screen Shot 2022-09-18 at 6 30 04 PM](https://user-images.githubusercontent.com/88747464/190930611-68f370a8-2429-45c6-8ea6-d73652de1262.png)

### Findings

* Interactive Map

![Screen Shot 2022-09-17 at 11 37 23 PM](https://user-images.githubusercontent.com/88747464/190930473-36f85af5-8183-42b4-8f70-ed28dd56dd78.png)


## 2. Choose the Right Flight

[Click here for a detailed version.](https://github.com/calistad/Client_travel_plan/blob/main/Airline_Analysis.md)

### Approach

A dataset with 9 columns and 539,383 rows.

![Screen Shot 2022-07-14 at 8 38 29 PM](https://user-images.githubusercontent.com/88747464/179123844-6d430fa6-1459-45c8-bbbf-f90aeeca0c96.png)

45% of the flights are delayed and 55% of the flights are on time.

![Screen Shot 2022-07-14 at 8 41 14 PM](https://user-images.githubusercontent.com/88747464/179124142-0fd60e3e-c515-4f89-aa9c-0569d1ee65ba.png)

![Screen Shot 2022-07-14 at 8 41 23 PM](https://user-images.githubusercontent.com/88747464/179124183-a0f0fad1-06b7-4f4b-ae2e-c1b24d87097b.png)
![Screen Shot 2022-07-14 at 8 41 30 PM](https://user-images.githubusercontent.com/88747464/179124192-aec473ce-2298-44eb-827e-683953aa0b83.png)

Flights with shorter times tend to be on time.

![Screen Shot 2022-07-14 at 8 45 53 PM](https://user-images.githubusercontent.com/88747464/179124641-bc37d799-2f6e-48da-bf3a-7490594e5264.png)
![Screen Shot 2022-07-14 at 8 46 07 PM](https://user-images.githubusercontent.com/88747464/179124657-3df4c126-9a88-4d6b-ada1-e0d6315a7961.png)

WN airline has the most count of flights and the most amount of delays. YV airline has the least amount of delays.

![Screen Shot 2022-07-14 at 8 51 22 PM](https://user-images.githubusercontent.com/88747464/179125026-1c1ecbc0-af50-4c80-8e22-263e968b4e9a.png)
![Screen Shot 2022-07-14 at 8 51 29 PM](https://user-images.githubusercontent.com/88747464/179125031-9802d7b2-a0de-406b-a75c-da082de0934f.png)

Prepared dataset after categorical data encoding.

![Screen Shot 2022-07-14 at 8 54 27 PM](https://user-images.githubusercontent.com/88747464/179125294-428f7938-1110-47cc-ab0b-b0e3d252869f.png)

## Findings

Retrieve **Feature importance**.

![Screen Shot 2022-07-14 at 9 44 08 PM](https://user-images.githubusercontent.com/88747464/179130183-ff3de576-8132-4b60-9fb3-2b61449a0cb9.png)

The most significant features are `Airlines`, `Time`, `Airport_To`, `Flight`.

![Screen Shot 2022-07-14 at 10 07 29 PM](https://user-images.githubusercontent.com/88747464/179132435-61a32d57-54ef-407c-829b-4981eea98e10.png)

The model with the best performance is the voting classifier, however, it tends to be more computationally intensive.

Therefore, both the `voting classifier` and `ada boost classifier` are recommended in this case.

| Voting Classifier | Ada Boost |
| --- | --- | 
| Accuracy: 66.3% | Accuracy: 64.8% |
| ![Screen Shot 2022-07-14 at 9 55 40 PM](https://user-images.githubusercontent.com/88747464/179131315-618b0966-261c-44ca-ab45-3dce97f0d786.png) | ![Screen Shot 2022-07-14 at 10 01 32 PM](https://user-images.githubusercontent.com/88747464/179131895-49dd23b8-1148-4c33-be20-e5b9f32ce083.png) |
| ![Screen Shot 2022-07-14 at 9 55 46 PM](https://user-images.githubusercontent.com/88747464/179132124-10bc6486-c220-4807-9843-83fcfca35721.png) | ![Screen Shot 2022-07-14 at 10 01 37 PM](https://user-images.githubusercontent.com/88747464/179132159-57849670-43ed-49a6-8a6d-7e7968df0c40.png) |
| ![Screen Shot 2022-07-14 at 9 55 54 PM](https://user-images.githubusercontent.com/88747464/179131354-6f499712-149c-4716-8b5b-086bf1c1a7ba.png) | ![Screen Shot 2022-07-14 at 10 01 45 PM](https://user-images.githubusercontent.com/88747464/179132024-b8f6e71e-c0aa-4fb9-b35c-67cda845a370.png) |
| ROC AUC: 71% | ROC AUC: 69.4% |
| ![Screen Shot 2022-07-14 at 9 56 03 PM](https://user-images.githubusercontent.com/88747464/179131374-dbe4c373-3db8-4294-b46e-efe3e2deef47.png) | ![Screen Shot 2022-07-14 at 10 01 54 PM](https://user-images.githubusercontent.com/88747464/179132035-46448ae0-f408-40e2-9354-9ad528f20521.png) |


## 3. Reserve the Suitable Airbnb

Assuming the client chooses Los Angeles, we will look at Airbnb located in Los Angeles.

### Approach

13,000+ hotels for clients to choose.

![Screen Shot 2022-09-18 at 6 58 49 PM](https://user-images.githubusercontent.com/88747464/190931914-746a400c-51b8-4467-bc14-85047ec284bb.png)

* Clients' requirements.

![Screen Shot 2022-09-18 at 6 59 12 PM](https://user-images.githubusercontent.com/88747464/190931927-55b6ed4e-a684-4490-bfa4-c9bedfdf6b5e.png)

Available hotels after clients' requirements.

![Screen Shot 2022-09-18 at 6 59 46 PM](https://user-images.githubusercontent.com/88747464/190931930-b8894de2-495e-4de4-967a-418d2060496a.png)


## 4. Estimate the Potential Housing Price

Assuming the client chooses Los Angeles, we will predict Airbnb pricing located in Los Angeles.

### Approach

![Screen Shot 2022-09-18 at 7 15 35 PM](https://user-images.githubusercontent.com/88747464/190932365-c6bb1120-2f4a-4779-ac15-d0c3785c910d.png)

![Screen Shot 2022-09-18 at 7 15 48 PM](https://user-images.githubusercontent.com/88747464/190932371-a5a19b56-8eae-47a4-8223-605afa144fdf.png)

![Screen Shot 2022-09-18 at 7 16 07 PM](https://user-images.githubusercontent.com/88747464/190932374-5236a976-f596-4a1f-9306-b6f066004fbc.png)

Retrieved **Feature importance**.

![Screen Shot 2022-09-18 at 7 19 11 PM](https://user-images.githubusercontent.com/88747464/190932459-f384a04f-d3e6-40bf-ae41-6c942aaa79b6.png)
![Screen Shot 2022-09-18 at 7 19 31 PM](https://user-images.githubusercontent.com/88747464/190932464-3261ab83-3f38-4dd0-aa0d-8bd35aa1cd82.png)

The most significant features are `Cleaning_fee` and `bedrooms`.

![Screen Shot 2022-09-18 at 7 16 41 PM](https://user-images.githubusercontent.com/88747464/190932379-eadb10c6-65bc-4c4a-a3b7-fd1b36580bdc.png)

Linear regression would be recommended for its most accurate performance. 

Ridge Regression with Grid Search Cross-validation achieved the second best performance.

| Linear Regression | Ridge Regression |
| --- | --- | 
| Accuracy: 61% | Accuracy: 59% |
| Residual Standard Error: 147.39 | Residual Standard Error: 171.09 |
| ![Screen Shot 2022-09-18 at 8 59 46 PM](https://user-images.githubusercontent.com/88747464/190935820-572325d3-74ef-4af9-8faa-3d612d8349f7.png) | ![Screen Shot 2022-09-18 at 8 59 57 PM](https://user-images.githubusercontent.com/88747464/190935830-bec27d74-1baf-4334-9dbf-52c4fb95a6ca.png) |


## Resources

Airlines Dataset to predict a delay. (2022, June 21). Kaggle. https://www.kaggle.com/datasets/jimschacko/airlines-dataset-to-predict-a-delayMicrosoft. (2022).

C. (2020, April 13). Voting Regressor with Pipelines. Kaggle. https://www.kaggle.com/code/cerberus4229/voting-regressor-with-pipelines/notebook

C. (2021, September 21). Feature importance using the LASSO. Kaggle. https://www.kaggle.com/code/carlmcbrideellis/feature-importance-using-the-lasso

Get the Data. (n.d.). Retrieved September 18, 2022, from http://insideairbnb.com/get-the-data/

Kumar, A. (2022, April 24). Lasso Regression Explained with Python Example. Data Analytics. https://vitalflux.com/lasso-ridge-regression-explained-with-python-example/

Ray, S. (2020, June 26). 8 Proven Ways for improving the “Accuracy” of a Machine Learning Model. Analytics Vidhya. https://www.analyticsvidhya.com/blog/2015/12/improvemachine-learning-results/
