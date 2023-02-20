# EDA

## Correlation of Features

![image-20230219203623948](/Users/aaronlalala/Documents/Courses/UIUC/IE 517/Code-IE-517-ML-in-Finance/IE517_S23_HW4/corr_matrix.png)

The above the the correlation matrix visualized by heat map. From the plot we can clearly see that first 13 features have weak correlation with all other features and response. This aligns with the fact that those features are randomly generated.

## Scatter Plots of Noises

![image-20230219204114153](/Users/aaronlalala/Documents/Courses/UIUC/IE 517/Code-IE-517-ML-in-Finance/IE517_S23_HW4/pair-scatter-random.png)

The above is the pairwise scatter plot generated using Seaborn using first 13 generated random features. You could see that those data are even distribution the x and y axis for each pair of them, indicating they are independent with each other.

## Scatter Plot of Features

![image-20230219204228633](/Users/aaronlalala/Documents/Courses/UIUC/IE 517/Code-IE-517-ML-in-Finance/IE517_S23_HW4/pair-scatter-feature.png)

The above is the pairwise scatter plot generated using actual collected data. You could clearly see the differences with the one that plotted using noises. Some data are discrete some are continuous. Also the response has significant correlation with them.



# Linear Regression

The following is the coefficient plot:

![image-20230219210306350](/Users/aaronlalala/Documents/Courses/UIUC/IE 517/Code-IE-517-ML-in-Finance/IE517_S23_HW4/regcoef.png)

- The intercept of the model is 29.01
- Testing mse: 26.63
- Testing R2 is 0.605

The following is the residual plot:

![image-20230219213111938](/Users/aaronlalala/Library/Application Support/typora-user-images/linear-residual.png)

# Ridge Regression

![image-20230219210453114](/Users/aaronlalala/Library/Application Support/typora-user-images/alpha-select-ridge.png)

From the plot we could see that no matter how we set the strength of regularization. We can't separate noise from features.

The following is the coefficient plot:

![image-20230219212749211](/Users/aaronlalala/Library/Application Support/typora-user-images/ridge-coef.png)

- The intercept is 24.22
- Testing mse: 26.82
- Testing R2: 0.603

The following is the residual plot:

![image-20230219213011325](/Users/aaronlalala/Library/Application Support/typora-user-images/ridge=residual.png)

# LASSO Regression

From the plot we could see that LASSO model is good at filtering useful features. It successfully separate the noise features at alpha =1.

![image-20230219212849290](/Users/aaronlalala/Library/Application Support/typora-user-images/lasso-alpha.png)

The following is the coefficient plot:

![image-20230219212820520](/Users/aaronlalala/Library/Application Support/typora-user-images/lasso-coef.png)

- The intercept is 34.94
- Testing mse 24.4
- Testing R2: 0.56

The following is the residual plot:

![image-20230219213047725](/Users/aaronlalala/Library/Application Support/typora-user-images/lasso-residual.png)

# Conclusion

Genearlly, Ridge model is not good at feature selecting. Though, it could optimize and give us a genearlly good prediction, it's hard when we try to interpreting the features. (Since we might want to make some decisions, i.e. buy houses). On the other hand, LASSO clearly tell us what features are bad and should be exluded. It actually turns out drop most of the noise features. 

Finally, after fitting the LASSO model, we could manually drop those bad features and fit linear regression model again. The process could give us better prediction and R2.