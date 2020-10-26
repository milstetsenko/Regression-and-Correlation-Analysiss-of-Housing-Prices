# Regression-and-Correlation-Analysiss-of-Housing-Prices
## Introduction:
This dataset contains house sale prices for King County, WA. It includes the homes sold from May 2014 to May 2015 by harlfoxem (Harlfoxem). The research question chosen for this dataset is: ​How can I best predict the market price of the house, knowing the trends of the previous sales, not to be tricked by overpricing of realtors? I will use python, Data Science learning materials, and OpenIntro (Diez) to conduct the most precise research and to automate the findings.
## Dataset:
​ I retrieved the dataset from Kaggle. The variables chosen for the analysis are the ones that most often can be found on the real estate websites, so the regular person without the need to obtain any additional information can estimate the price of the house. The initial predictor variables are quantitative discrete: a number of bedrooms, number of bathrooms; quantitative continuous: square footage of the house, squared footage of the basement, and the year the house was built; and qualitative categorical: the condition of the house. The response variable is the price (continuous quantitative). It is important to identify the types of the variable to properly
interpret the regression line (for categorical variable). No cleaning for the data was needed.
 
 ## Correlation and Regression
I computed a heatmap to see the distribution of correlations between all the variables to identify the multicollinearity.

![Screenshot](https://github.com/milstetsenko/Regression-and-Correlation-Analysiss-of-Housing-Prices/blob/master/Screen%20Shot%202020-10-26%20at%208.55.49%20PM.png)


   Figure 2. The heatmap plot showing the correlation between the input variables. From the plot, one can see the stronger correlation between footage and number of bathrooms, the age and number of bedrooms.... The heatmap is time-efficient showing all the correlation and helps identify potential elimination instead of plotting all the scatterplots2


From the heatmap, I can see that sqft_living is strongly correlated to the number of bathrooms, and yr_built is strongly correlated to the condition of the house. Sqft_living also has a strong correlation with the number of bedrooms and yr_built with the number of bathrooms. Further on, I will use this information to conduct the correlation plots and to eliminate these variables. Using both number bedrooms and bathrooms seem redundant to the plot because of multicollinearity.
The R -squared value for y_built vs sqft_living is 0.101, showing there is no multicollinearity, so I want to leave both of the variables in the model.
The R-squared value for a number of bathrooms against bedrooms is 0.27, therefore, Pearson’s r is =0.52 - it is a moderate positive correlation, so I will need to take out one of the

  
 Further examining the data, I learned that the number of bathrooms does not improve the R squared value of the multiple regression, therefore I eliminate this variable).

#### Checkpoint: 7 independent variables: 'bedrooms', 'sqft_living', ‘yr_built, 'sqft_basement’,‘bedrooms’, ‘condition’, ‘bathrooms’.

Before computing the multiple regression, I need to check the assumptions: the normality of the residuals, the constant variability of the residuals, independence of residuals, and the linear correlation of each of the variable to the response variable.
### Linear correlation to the response variable:




Figure 3: The part of the pair plot outputting the correlation plots of all the predictor variables against the response variable. Each of the plots represents a predictor variable plotted against the response variable - price.
Looking at the pair plot (top row prices against the rest of the predictor variables), (Appendix C) (Seaborn Pydata, n.d), a number of bedrooms against prices are not linear (Appendix C), also the residuals (average distance of the factual data from the model’s prediction) have the reverse hyperbolic pattern, most of the residuals are concentrated below with many outliers on top.
Sqft_living against prices is not ideal (Appendix C), because the data is somewhat heteroscedastic, but I will proceed with skepticism because the overall trend is linear, R squared


Sqft_basement against prices is not ideal either because it contains many 0 values (Appendix C). However, I will need to proceed with backward selection to make sure this variable contributes to the R-squared.

 
 Correlation and Regression
Condition vs prices does not show any correlation at all (and R-square is 0), so I can take it out of the model. 
The normality of the residuals:
Checkpoint: I have 4 remaining independent variables: 'bedrooms','sqft_living', 'sqft_basement’, ‘yr_built’.
As I can see from the normal probability plot (Appendix D), the residuals are not normal, not satisfying the condition for the model (the tails are too heavy). Hence, it is not reliable to use the model to predict the prices of the houses for sale. All the combinations of the predictor variable produce the unfit QQ plot. For the purpose of this assignment, I will continue inferencing from the model to perform the required steps of the assignment.
Constant Variance: The condition is not satisfied, either, the plot is not football-shaped, the data is heteroscedastic 
Independence: I do not know how the data was collected, the data was collected for a certain period of time (from May to May), therefore, there is no assurance that it is independent.
Multiple regression:
Backward elimination:
Using the backward elimination method, I first computed all the variables in the regression model. I want to compare the R squared value of the equation with and without sqft_basement, because it might repeat the patterns of the sqft_living but is not shown on the feet map since not all of the houses have the basement. The R squared value is 0.507 without the basement variable dropping only by 0.01 points. This is an insignificant drop and it simplifies

#### Checkpoint: 3 predictor variables: footage of the house, year the house was built in, and the number of bedrooms.


Both of the P-values of the slopes are 0.00, confirming the idea that the variables are
statistically significant to the model, which is consistent with the fact that if we take out any one
of the two variables out of the model, the R-squared value will drop significantly. The practical
significance: the R-squared value is 0.507. One can explain 50.7% of variance using these
variables when predicting the price of the home based on the footage and the number of

Confidence intervals.
Further on, I will construct confidence intervals for the slope of the regression line.
Figure 4: The output of the multiple regression function, showing all the data necessary to make inferences about the model and justifying practical significance - the R-squared value.
From this report, I can derive the 95% confidence interval:
For the number of bedrooms: [-6.16e+04;-5.25e+04].
For the footage of the house: [309.367;318.530].
It means that if the data collection was repeated many times, 95% of the confidence intervals created would contain the population mean.

## Results and Conclusions
I have obtained the prediction model based on its footage and the number of bedrooms. The population data is the whole state of Washington, however, the results might differ based on the area, because the King county includes Seattle - a more densely populated area, implying that the prices might be higher. One need to be cautious to avoid hasty generalization. The coefficient might be introduced as a measure of adapting to the demand on the houses or the location of the houses for it to be generalized to other areas. This needs to be further hypothesized and researched. The model does not prove that the prices rise/drop is caused by the number of bedrooms and the footage, only that it is correlated, however, it seems like a logical explanation.

To prove the causation, one needs to conduct further research. The model, however, cannot be relied on: the conditions for conducting linear regression were not fulfilled - the induction is
weak. If no other model for predicting the model exists and the need for the model is sufficient, one may proceed with caution. Also, the model does not account for the extrapolation, and if the houses are out of price range of those examined in the report, then one must once again proceed with caution with the absence of better models.
