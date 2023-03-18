# Car Prices Data Exploration and Modeling

This project aims to gain insights into the pricing of cars by exploring explanatory variables and creating models to predict the response variable. The analysis was performed on a dataset containing information on car prices. The following sections describe the techniques applied and results obtained for data preparation and exploration, including statistical inference and modeling techniques. Everything has been computed through **R**.

The following is a brief summary of each section from the report. For more details, see the [pdf](reports/SIM_Assignment_1.pdf).

## TOC

- [Problem Statement](#problem-statement)
- [Data Collection and Cleaning](#data-collection-and-cleaning)
- [EDA](#eda)
  * [Outlier Detection](#outlier-detection)
  * [Response Variable: Price](#response-variable--price)
  * [Quantitative Explanatory Variables](#quantitative-explanatory-variables)
  * [Qualitative Explanatory Variables](#qualitative-explanatory-variables)
  * [Imputation](#imputation)
- [Modeling](#modeling)
  * [Normality Test and Serial Correlation](#normality-test-and-serial-correlation)
  * [Variable Correlation](#variable-correlation)
  * [Polytomic Factor](#polytomic-factor)
  * [ANOVA Model](#anova-model)
  * [Interaction Effects](#interaction-effects)
  * [Linear Regression Model with Age](#linear-regression-model-with-age)
  * [Quadratic Term Model](#quadratic-term-model)
  * [Exploratory Numeric Variables](#exploratory-numeric-variables)
  * [Final Model](#final-model)
  * [Logarithmic Model](#logarithmic-model)
  * [Main Effects from Factors](#main-effects-from-factors)
  * [Graphical Assessment of Best Model](#graphical-assessment-of-best-model)
  * [Presence of Outliers in Studentized Residuals](#presence-of-outliers-in-studentized-residuals)
  * [Presence of A Priori Influential Data Observations](#presence-of-a-priori-influential-data-observations)
  * [Presence of A Posteriori Influential Values](#presence-of-a-posteriori-influential-values)
  * [Expected Price with 95% Confidence Interval](#expected-price-with-95--confidence-interval)
- [Conclusion](#conclusion)

## Problem Statement

The project's goal is to gain insights on the price of cars using the exploratory variables and create models to explain or predict this response variable.

## Data Collection and Cleaning

The following steps were performed for data preparation and cleaning:

1. The four homogeneous datasets are merged into a single one.
2. Structural errors are fixed: categorical values are mutated into factors, and extra blanks are removed in Model.
3. Duplicated observations are removed.
4. A random sample of 5000 observations is selected.
5. Year variable is transformed into Age.
6. Wrongly classified cars are labeled as electric according to their engine size.
7. Missing values are explored. 0 NA’s are found.

## EDA

The following exploratory data analysis was performed:

### Outlier Detection

Outlier detection was first performed with a univariate exploration and then with a multivariate one. A new attribute, Outliers, was created in the dataset to keep track of the number of univariate outliers each individual has. Observations which only have one univariate outlier (based on *IQR*) are imputed with NA while the ones with more are kept so the multivariate outliers do not become biased. All the individuals with more than one univariate outlier have been detected with the *Mahalanobis* distance, and thus, have been removed from the main analysis.

### Response Variable: Price

46 outlying observations (0,9%) were completely removed, as they can highly influence our models and analyses.

### Quantitative Explanatory Variables

It has been observed that all variables have extreme outliers and that tax is the only one which has outliers in both tails.

### Qualitative Explanatory Variables

Regarding qualitative variables, both `transmissionType` and `manufacturer` have not displayed any interesting remarks, having 3 and 4 distinct categories respectively and no significant count differences. The remaining three variables, however, have been assessed differently.

### Imputation

After finding all the outliers, the imputation of the missing values is the step which follows. First of all, quantitative variables are managed: *PCA* imputation is applied; then, it is checked whether the imputed values are incoherent (e.g., nega`fuel type`tive `age`) or not, and tested if the distribution of the values is preserved, which it is. After that, categorical variables are dealt with. *MCA* imputation is applied; similarly, it is checked if the proportions of the variables remain the same after the imputation process.

## Modeling

The following topics were addressed during the modeling phase:

### Normality Test and Serial Correlation

The normality of the response variable price was assessed using a *Shapiro-Wilk* test and visualizations, which revealed that the response variable does not follow a normal distribution. The *Durbin-Watson* test was used to detect serial correlation in the response variable, which was found to be present.

### Variable Correlation

Quantitative and qualitative variables were examined for their association with the response variable (price). *Spearman* correlation was used for non-normal data, and a *Kruskal* test was used for categorical data. It was found that `mileage`, `mpg`, and `age` had a negative correlation with `price`, while `tax` had a positive correlation. Qualitative variables (`transmission`, `fuelType`, and `enginezise_int`) were also found to be significantly associated with `price`.

### Polytomic Factor

The `age` variable was discretized into quartiles to create a new factor, `f.age`. The downward trend of the price with increasing age was confirmed through visualizations, a *Kruskal* test, and a pairwise *Wilcox* test.

### ANOVA Model

An *ANOVA* model was used to explain car `price` according to the `age` factor and `fuel type`. The `age` factor was found to have a more significant effect than `fuel type`. The coefficients of the resulting model showed that older cars have a lower predicted price, and hybrid cars have a higher price than diesel or petrol cars.

### Interaction Effects

The *ANOVA* model was extended to include the interaction between the `age` factor and `fuel type`. It was found that the relation between `price` and `age` was affected by `fuel type`, and the adjusted R-squared barely increased with this extension. The interaction plot revealed that while the price of all `fuel type`s decreases with the `age` of the car, the `price` is also influenced by `fuel type`. Specifically, petrol cars were always the cheapest, and the `price` trend reversed for old hybrid and diesel cars.

### Linear Regression Model with Age

The linear regression model between `price` and `age` showed a high intercept and a negative slope, with an R2 of 0.39. However, the model had a high deviation from normal distribution and had problems with granularity.

### Quadratic Term Model

The addition of a quadratic term to the linear regression model showed a slight improvement in residuals, but the model was not statistically significant.

### Exploratory Numeric Variables

Adding additional numeric variables showed that the `mileage` variable was not significant, and the `mpg` variable required a transformation. After transformations, `age` and `mpg` were the variables that contributed the most to the model.

### Final Model

The best model included `age`, `mpg`, `manufacturer`, `engine size`, `transmission`, and `fuel type`, with an R2 of 0.80. The residual plots showed some deviations from linearity and normality, but the model was suitable for modeling the price.

### Logarithmic Model

The logarithmic model with a transformation on the response variable showed improvements in residuals and a statistically significant result for the `tax` variable. After transformations, `mpg` and `age` required an additional transformation.

Overall, the final model with `age`, `mpg`, `manufacturer`, `engine size`, `transmission`, and `fuel type` was the best perfirming one, with an R2 of 0.80.

### Main Effects from Factors

Using the step function, it was found that all additional factors are worth keeping, and collinearity effects were not observed. With the addition of factors, R2 increases to 0.86.

### Graphical Assessment of Best Model

The residuals and standardized residuals do not show a pattern, indicating that the linear and homoscedastic assumptions hold. However, normality problems were observed in the left tail, and a small group of observations can be influential. The marginal plots display that the model fits the points well in comparison to a smoother.

### Presence of Outliers in Studentized Residuals

69 outliers were found using both inferential and descriptive methods. The car model "Up" manufactured by VW is overrepresented in the outliers, accounting for over 30% of them. The other outliers are manual cars fueled by petrol with a lower price.

### Presence of A Priori Influential Data Observations

77 values with significantly high leverage were obtained, and they were all hybrid cars that were newer, not manual, more expensive, and with a small engine size.

### Presence of A Posteriori Influential Values

247 values were obtained using *Cook*'s distance, and none of the observations had a distance greater than 0.5 when considering the sample as large enough and discarding the *Chatterjee and Hadi* cut-off.

### Expected Price with 95% Confidence Interval

The predicted `price` for a 5-year-old car with the rest of numerical variables on the mean and factors on the reference level was 13844.91£, with a confidence interval of (10017.85£, 19133.99£). Although the prediction output is coherent, the interval range is quite broad.

## Conclusion

This project successfully modeled car prices using various variables, ensuring a quality dataset. The final model explained 86% of the variance in car prices, indicating that older cars tend to have lower prices and hybrid cars have higher prices than diesel or petrol cars. Outliers and missing values were managed, and the model was deemed suitable for car pricing despite some deviations from linearity and normality. This project demonstrates the effectiveness of using statistical techniques to analyze complex datasets.
