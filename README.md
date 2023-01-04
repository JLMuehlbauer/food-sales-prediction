# Food Item Sales
## Analysis and prediction of food item sales across outlets

**Author**: Jackson Muehlbauer

### Business problem:

From both the perspective of a wholesale food supplier and a retail food seller, it is important to have an understanding of how well a particular item will sell. Having the ability to predict the amount of sales for a particular item will allow both of the interested parties to maximize profit and minimize risk. That said, there are many variables that have the potential to impact an item's total sales, such as the type of food, the size of the outlet it is being sold at, etc. Thus, scientific analysis and modeling is vital in improving the prediction capabilities for either the wholesale supplier and the retail seller. 


### Data:
The raw data contained 8523 entries and 12 columns. The column names and descriptions are displayed in dictionary below.
#### Data Dictionary:
![sample image](outlet_sales_dict.png)


## Methods
The data was prepped for analysis by checking for duplicated rows and missing entries for each feature. The unique values for the categorical features were checked for any inconsistencies, to which these were fixed using best judgement. For both the data exploration and machine learning portions of this exercise, missing values were imputed, although different methods were employed for each to prevent data leakage. After cleaning the data, the data was  explored and explained. 

### Exploratory Data Analysis
#### Numerical Features
- Plotted as a histogram to btter understand their distribution. 
- Plotted as a correlation heatmap to understand any correlations to other features and to the target

![sample image](Item_Visibility_histogram.png)
> The image above shows the distribution to the item's visibility. From this histogram, it was observed that this feature is very left-skewed and most items appear to have very little visibility. 

#### Categorical Features
- Plotted as multivariate boxplots with respect to the Item_Outlet_Sales. This gave some insight as to which features could be useful in our model. 
- Plotted as frequency bar plots. This gave some insight as to which categories were most common in each feature.
![sample image](Item_Type_Bar.png)
> The image above shows the counts for each item type. From this, it was noticed that certain types, like fruits and vegetables, are much more ubiquitous  than other types, like seafood. This may indicate that not all stores carry the less common item types, or that there is a larger variety of fruits and vegetables than seafood.

### Explanatory Data Analysis
- After the exploratory analysis, figures were made to show the most highly correlated features with respect to the Item_Outlet_Sales and some other interesting insights provided by the features.

![sample image](Outlet_Type_Bars.png)
> Interpretation:
Subplot 1: Supermarket Type3 has the highest average item outlet sales. This indicates that this outlet type sells a higher volume of a given item than the other outlet types. Likewise, Grocery stores sell the lowest volume of any given item.
Subplot 2: Supermarket Type1 has the highest total sales. From subplot 1, we know that the Supermarket Type3 has the highest average item sale, which suggests that Supermarket Type1 has the highest number of unique items.
Subplot 3: Supermarket Type1 has the highest number of estimated sales (assuming items were sold at the Maximum Sale Price).

## Machine Learning
The following modeling techniques were used:
- Linear Regression
- Single Decision Tree

*Note: Prior to running these models, ordinal features were ordinally encoded, nominal feature were imputed with the most frequent category and one hot encoded, and numerical features were imputed with the mean and scaled with standard scaling. 

### Linear Regression
- The R-squared value for the train and test sets are 0.5601 and 0.5685, respectively.
- The root mean squared error value for the train sets and test are 1141.03 and 1091.05, respectively.

### Default (pre-tuning) Decision Regression Tree
- The R-squared value for the train and test sets are 1.0 and 0.1944, respectively.
- RMSE was not calculated prior to tuning.

### Tuned Decision Regression Tree (max depth = 5)
- The R-squared value for the train and test sets are 0.6039 and 0.5947
- The RMSE value for the train and test sets are 1082.66 and 1057.42

![sample image](r-squared_modelDepth.png)
> The optimal depth according to the R-squared value for the test set was found to be 5, as shown in the figure. 


## Model Recommendations:

The recommended model is the tuned decision regression tree over the linear regression.

Overall, the single decision regression tree performed slightly better than the linear regression in both R-squared and RMSE calculated from the test set.

The test set R-squared for the single decision tree was 0.5947 while the same metric for the linear regression model was 0.5685. The higher value for decision tree indicates that the model better can better explain the variance in the item outlet sales with the available features.

The test set RMSE for the decision tree was $1057.42, the same metric for the linear regression was $1091.05. These are very close in value but there is still a slight edge for the decision tree. Overall, the decision tree predicts with slightly lower residuals (when punishing large error predictions)


## Limitations & Next Steps

As stated previously, this single decision regression tree is far from perfect; the low R-squared values for both the train and test data shows that this model has high bias. The RMSE values also show that the model makes predictions with large residuals, especially when compared to the average item outlet sales. The interested parties should be aware of the limitations of this model and leave room for some error. 

The next steps in obtaining a better model would be to try a random forest model on the data. This should improve the performance metrics as this model bootstraps, aggregates, and randomizes the allowable features in the decision tree. From the correlation heat map, only one numeric term was even moderately correlated to the item outlet sales. By randomizing the available features, there could exist some additional predictive power from the other features.

To improve the model even further, additional features could be measured and recorded. In theory, having more "useful" information to describe the target should improve the predictive capability of the model. For example, "organic" could be added as a feature to describe if the item is organic or conventional. That said, there is no guarentee that additional features will improve the model

### For further information


For any additional questions, please contact 
- Jackson Muehlbauer
- **jlmuehlbauer@gmail.com**
