

# OLS Regression Analysis Report

## Model Overview

This report provides the results of an **Ordinary Least Squares (OLS) Regression Analysis** conducted on the California housing dataset, with the dependent variable being **MedHouseVal** (median house value). The regression model aims to predict housing values based on several factors like median income, house age, average rooms, etc.

## Regression Results Summary

| Metric                       | Value       |
|------------------------------|-------------|
| **R-squared**                 | 0.606       |
| **Adj. R-squared**            | 0.606       |
| **F-statistic**               | 3970.0      |
| **Prob (F-statistic)**        | 0.00        |
| **Log-Likelihood**            | -22624.0    |
| **AIC**                       | 4.527e+04   |
| **BIC**                       | 4.534e+04   |
| **No. of Observations**       | 20640       |
| **Df Residuals**              | 20631       |
| **Df Model**                  | 8           |

### Coefficients

| Predictor       | Coef      | Std Err  | t       | P>|t|  | 95% Conf. Interval       |
|-----------------|-----------|----------|---------|-------|---------------------------|
| const           | -36.9419  | 0.659    | -56.067 | 0.000 | [-38.233, -35.650]        |
| MedInc          | 0.4367    | 0.004    | 104.054 | 0.000 | [0.429, 0.445]            |
| HouseAge        | 0.0094    | 0.000    | 21.143  | 0.000 | [0.008, 0.010]            |
| AveRooms        | -0.1073   | 0.006    | -18.245 | 0.000 | [-0.119, -0.096]          |
| AveBedrms       | 0.6451    | 0.028    | 22.928  | 0.000 | [0.591, 0.700]            |
| Population      | -3.976e-06| 4.75e-06 | -0.837  | 0.402 | [-1.33e-05, 5.3e-06]      |
| AveOccup        | -0.0083   | 0.002    | -4.769  | 0.000 | [-0.012, -0.005]          |
| Latitude        | -0.4223   | 0.007    | -58.541 | 0.000 | [-0.435, -0.410]          |
| Longitude       | -0.4345   | 0.008    | -57.682 | 0.000 | [-0.449, -0.420]          |


### Model Diagnostic Tests

- **Omnibus Test**: 4393.650
- **Prob (Omnibus)**: 0.000
- **Durbin-Watson**: 0.885
- **Jarque-Bera (JB)**: 14087.596
- **Prob (JB)**: 0.000
- **Skew**: 1.082
- **Kurtosis**: 6.420
- **Condition Number**: 2.38e+05

## Interpretation of Results

### 1. R-squared and Adjusted R-squared
- **R-squared**: 0.606, which means that **60.6% of the variance** in housing prices (MedHouseVal) is explained by the predictors in the model.
  - **Best Value**: An R-squared of **1.0** would indicate that the model explains all the variance in the data perfectly.
  - **Worst Value**: An R-squared of **0** would indicate that the model explains none of the variance, meaning it is not a useful model.
- **Adjusted R-squared**: 0.606, which adjusts the R-squared for the number of predictors in the model.
  - **Best Value**: Close to 1.0, suggesting the model performs well even with added predictors.
  - **Worst Value**: Close to 0 or negative, which suggests the model is overfitting or the additional predictors do not improve the model.

**Assumption**: These values assume a linear relationship between the predictors and the target variable. A low R-squared could suggest that a non-linear model might be more appropriate.

### 2. F-statistic and Prob (F-statistic)
- **F-statistic**: 3970.0, indicating the overall significance of the model.
  - **Best Value**: A large F-statistic indicates that at least one of the predictors is significantly related to the target variable.
  - **Worst Value**: A low F-statistic suggests that none of the predictors contribute meaningfully to the model.
- **Prob (F-statistic)**: 0.00, indicating that the model is statistically significant (p < 0.05).
  - **Best Value**: Close to 0, meaning the model is highly significant.
  - **Worst Value**: Close to 1, meaning the model is not significant.

**Assumption**: This tests whether any of the coefficients in the model are significantly different from zero. A low F-statistic or high p-value suggests that none of the variables significantly explain the variance.

### 3. Log-Likelihood (-22624.0)
- **Log-Likelihood**: The value of -22624.0 indicates how well the model fits the data.
  - **Best Value**: A higher (less negative) log-likelihood indicates a better-fitting model.
  - **Worst Value**: A very low log-likelihood suggests the model does not fit the data well.

**Assumption**: The log-likelihood is based on the assumption that the residuals (errors) are normally distributed. Deviations from normality can reduce the log-likelihood.

### 4. AIC (Akaike Information Criterion: 4.527e+04) and BIC (Bayesian Information Criterion: 4.534e+04)
- **AIC**: 45,270 and **BIC**: 45,340 are used to compare models, penalizing complexity (number of predictors).
  - **Best Value**: Lower values are better, as they balance model fit and complexity.
  - **Worst Value**: Higher values indicate the model is either a poor fit or overly complex.

**Assumption**: These criteria assume that simpler models are preferable to more complex ones, all other things being equal. A lower AIC/BIC value relative to other models would indicate better performance.

### 5. Coefficients and Interpretation
- **MedInc (0.4367)**: A 1-unit increase in median income results in a 0.4367 increase in median house value, holding other factors constant.
  - **Best Coefficient**: Positive values indicate an increase in house values.
  - **Worst Coefficient**: Negative values suggest a decrease in house values.
- **Population (-3.976e-06)**: Has a negligible and statistically insignificant effect on housing prices (p = 0.402).
  - **Best Coefficient**: The effect size is near 0, meaning it does not explain much variation in house prices.
  - **Worst Coefficient**: If statistically significant, negative values would suggest that larger populations decrease housing prices.

**Assumption**: Coefficients assume linear relationships between each predictor and the target. Non-linearity could lead to misleading interpretations.

### 6. Omnibus Test (Prob(Omnibus) = 0.000)
- **Omnibus Test**: Tests for the combined presence of skewness and kurtosis in the residuals.
  - **Best Value**: A **p-value > 0.05** suggests residuals are normally distributed.
  - **Worst Value**: A **p-value < 0.05** (as seen here) suggests residuals are not normally distributed.

**Assumption**: Normality of residuals. Violations indicate that the model may not be well specified.

### 7. Durbin-Watson (0.885)
- **Durbin-Watson**: Measures the presence of autocorrelation in residuals. A value of **2** indicates no autocorrelation.
  - **Best Value**: **Close to 2**, suggesting no autocorrelation.
  - **Worst Value**: Values closer to 0 or 4 indicate positive or negative autocorrelation, respectively.

**Assumption**: Independence of errors. The low value of 0.885 suggests positive autocorrelation, meaning that the residuals are not independent, violating a key assumption of OLS.

### 8. Jarque-Bera (Prob(JB) = 0.000)
- **Jarque-Bera Test**: Tests whether the residuals follow a normal distribution.
  - **Best Value**: A **p-value > 0.05** indicates normal residuals.
  - **Worst Value**: A **p-value < 0.05** (as seen here) suggests non-normality in residuals.

**Assumption**: This test assumes that the residuals should be normally distributed for valid inference in OLS. The significant p-value indicates a deviation from this assumption.

### 9. Skew (1.082) and Kurtosis (6.420)
- **Skew**: Measures asymmetry in the residual distribution.
  - **Best Value**: **0**, indicating a perfectly symmetrical distribution.
  - **Worst Value**: Positive values (like 1.082) suggest right-skewed residuals.
- **Kurtosis**: Measures the "tailedness" of the distribution.
  - **Best Value**: **3**, indicating normal kurtosis.
  - **Worst Value**: **6.420** indicates a higher kurtosis, meaning the residuals have fatter tails than a normal distribution, suggesting the presence of outliers.

**Assumption**: OLS assumes residuals are symmetrically distributed with normal tails. Deviations from these values suggest violations of normality.

### 10. Condition Number (2.38e+05)
- **Condition Number**: Measures multicollinearity (correlation between predictor variables).
  - **Best Value**: Values **< 30** indicate low multicollinearity.
  - **Worst Value**: Values **> 100** suggest severe multicollinearity. The condition number of 2.38e+05 (238,000) indicates extremely high multicollinearity.

**Assumption**: Low multicollinearity between predictors is an assumption of OLS. High multicollinearity can make it difficult to isolate the effects of individual predictors and leads to unstable coefficient estimates.

## Conclusion
This OLS regression model provides a moderately good fit for predicting median house values in California. Several variables, including median income, average bedrooms, and geographic location (latitude and longitude), are highly significant predictors. However, the model exhibits issues such as multicollinearity and non-normality of residuals, which may warrant further investigation or alternative modeling approaches (e.g., Ridge or Lasso regression) to improve the robustness of the predictions.
