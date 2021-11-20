# Predicting for how much should you sell your old car

Download the last [report](https://github.com/eReverter/cars_sim/blob/main/reports/exploration.html) and open it to vizualize its contents.

This is a project for the master in data science (MDS) taught at FIB, UPC. The aim of it is to predict for how much you should sell your old car. The data used for this prediction can be obtained through [kaggle](https://www.kaggle.com/adityadesai13/used-car-dataset-ford-and-mercedes). 

## Data

Only data from Audi, BMW, Mercedes and VW is going to be used. Also, only 5000 random samples from each subset are going to be kept. These are the requirements set by the university.

## Main To-Do

- [x] Get the data.
- [x] Merge the data.
- [ ] Explore each variable.
- [ ] Check missing values.
- [ ] Impute missing values.
- [ ] Check for outliers.

## Questions

- [ ] 1. Determine if the response variable (price) has an acceptably normal distribution. Address test to discard serial correlation.
- [ ] 2. Indicate by exploration of the data which are apparently the variables most associated with the response variable (use only the indicated variables).
- [ ] 3. Define a polytomic factor f.age for the covariate car age according to its quartiles and argue if the average price depends on the level of age. Statistically justify the answer.
- [ ] 4. Calculate and interpret the anova model that explains car price according to the age factor and the fuel type.
- [ ] 5. Do you think that the variability of the price depends on both factors? Does the relation between price and age factor depend on fuel type?
- [ ] 6. Calculate the linear regression model that explains the price from the age: interpret the regression line and assess its quality.
- [ ] 7. What is the percentage of the price variability that is explained by the age of the car?
- [ ] 8. Do you think it is necessary to introduce a quadratic term in the equation that relates the price to its age?
- [ ] 9. Are there any additional explanatory numeric variables needed to the car price? Study collinearity effects.
- [ ] 10. After controlling by numerical variables, indicate whether the additive effect of the available factors on the price are statistically significant.
- [ ] 11. Select the best model available so far. Interpret the equations that relate the explanatory variables to the answer (rate).
- [ ] 12. Study the model that relates the logarithm of the price to the numerical variables.
- [ ] 13. Once explanatory numerical variables are included in the model, are there any main effects from factors needed?
- [ ] 14. Graphically assess the best model obtained so far.
- [ ] 15. Assess the presence of outliers in the studentized residuals at a 99% confidence level. Indicate what those observations are.
- [ ] 16. Study the presence of a priori influential data observations, indicating their number according to the criteria studied in class.
- [ ] 17. Study the presence of a posteriori influential values, indicating the criteria studied in class and the actual atypical observations.
- [ ] 18. Given a 5-year old car, the rest of numerical variables on the mean and factors on the reference level, what would be the expected price with a 95% confidence interval?
- [ ] 19. Summarize what you have learned by working with this interesting real dataset.
