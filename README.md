# Fresh-Sales-Tool V3.0

### Goal: To predict daily sales of fresh products at a club-item level

### V1.0: implmented a moving average model

### V2.0: has three models running daily- ARIMAX, Holts-Winters and Neural Network

### V3.0: aimed at further improving the accuracy of prediction and also implementing a Bayesian framework to estimate safety stock

## Approach

### 1. Understanding the current state

### 2. Obtaining Baseline metrics for the current state
- Models trained for 2 years and tested on three weeks in May 2018 independently
- Results stored for future use 
- %MAPE of ~51% for 10 selected products
- Adding safety stock increases the %MAPE to 62%, and, has P(OOS) of 23% 

### 3. Feature Selection and Engineering
- New feature (Year+Month) to mimic the time space (could have done this daily, but, turns out, that tends to overfit models)
- Added a flag for first 5 days and first saturday of the month
- Added 3-day and 7-day moving average of price/quantity and price/item. The models picks on the price change from this

### 4. Bayesian Non-parametric approach- Gaussian Process
- Prior is a collection of gaussians, one for every finite collection of data
- Adjusts the posterior based on given data
- P(y/X) is a gaussian distribution for every X
- Can obtain the mean estimate and also the standard deviation from above

- %MAPE of 41%, a huge improvement over the existing process
- Adding safety stock increases %MAPE to 54% and has a P(OOS) of 27%

### 5. Other models: Multilayered Perceptron, Gradient Boosting
- Perform the best among all models
- MLP has a %MAPE of ~39%
- GB has a %MAPE of ~37%

### 6. Ensemble Approach
- Ensemble of ARIMAX, GP, MLP and GB
- Results pending