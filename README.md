# Fresh-Sales-Tool V3.0

(Cannot add code for proprietary reasons)

### Goal: To predict daily sales of fresh products at a club-item level

### V1.0: implmented a moving average model

### V2.0: has few time series approaches running daily. A Std. dev. based safety stock added

### V3.0: aimed at further improving the accuracy of prediction and also implementing a Bayesian framework to estimate safety stock

## Approach

### 1. Understanding the current state

### 2. Obtaining Baseline metrics for the current state
- Models trained for 2 years and tested on three weeks in May 2018 independently
- Results stored for future use 
- %MAPE of M% for 10 selected products
- Adding safety stock increases the %MAPE to S%, and, has P(OOS) of P% 

### 3. Selecting products for proof of concept
- Selected 12 products in a certain mid-US club
- Products chosen for diversity in departments and also on previous model performance

### 4. Feature Selection and Engineering
- New feature (Year+Month) to mimic the time space (could have done this daily, but, turns out, that tends to overfit models)
- Added flags for some observed patterns in shopping
- Added 3-day and 7-day moving average of price/quantity and price/item. The models picks on the price change from this

### 5. Bayesian Non-parametric approach- Gaussian Process
- Prior is a collection of gaussians, one for every finite collection of data
- Adjusts the posterior based on given data
- P(y/X) is a gaussian distribution for every X
- Can obtain the mean estimate and also the standard deviation from above

- %MAPE reduced by ~20%, a huge improvement over the existing process
- Adding safety stock increases %MAPE less than y% and has a P(OOS) slightly higher than before

### 6. Other models: Multilayered Perceptron, Gradient Boosting
- Perform the best among all models
- MLP has a %MAPE improvement of ~27%
- GB has a %MAPE improvement of ~28%

### 7. Ensemble Approach
- Ensemble of ARIMAX, GP, MLP and GB
- More robust than before with similar metrics
