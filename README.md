# Kaggle-Iowa-House-Prices

## Data Source
The data I used in this project is the Ames Iowa housing <a href='http://jse.amstat.org/v19n3/decock.pdf'>dataset </a>.
I downloaded the data from <a href='https://www.kaggle.com/c/house-prices-advanced-regression-techniques'>Kaggle</a> 
and submitted my predictions for scoring to that competition.

## Data Analysis
The first step of the analysis was looking at the data dictionary and learning what the obscure feature names and categories mean.
I found that some of the numerical features were meant to be categorical. I decided to make a dictionary of dtypes to be used when
creating the DataFrame. I also noted which categorical features were nominal and which were ordinal.

### Missing Data
There appear to be a lot of missing values when first looking at the DataFrame; however, the data dictionary told me that the value 
used to mark a feature such as a pool or a garage as not being present is NA. For the features where this is true, I created a new 
category called 'None' and assigned all of the NA to it. For the categorical features where this was not the case, I filled with the
most common value. The only numerical features with missing values are 'LotFrontage' and 'GarageYrBlt.' I filled the lot frontage with the median value. I used 9999 for the year the garage was built because those homes did not have a garage.

### Univariate Analysis
For the numeric features, most are not close to being normal at all. Those that are somewhat close often have long tails.
![](https://github.com/MikeMcFall/Kaggle-Iowa-House-Prices/blob/master/code/SalePrice%20Analysis_files/SalePrice%20Analysis_16_0.png)
Many of the categorical features are dominated by a single category.
![](https://github.com/MikeMcFall/Kaggle-Iowa-House-Prices/blob/master/code/SalePrice%20Analysis_files/SalePrice%20Analysis_21_0.png)

### Bivariate Analysis
There are several features with a Pearson correlation to the sale price >0.5. The graphs are plotted in order of decreasing 
correlation going to the right and down. The most well-correlated feature to the sale price is the ground living area.
![](https://github.com/MikeMcFall/Kaggle-Iowa-House-Prices/blob/master/code/SalePrice%20Analysis_files/SalePrice%20Analysis_25_1.png)

## Machine Learning
Since the challenge is to predict a continuous variable, I beagan by using a simple linear regression which did not perform very well 
when compared to all the other entries. I trained regularized linear regressions as well, but they only provided marginal improvements 
in the scoring. The next model I used was random forests which greatly impoved the scoring of the predictions. The final model type 
I used was a gradient boosted forest. This again was an improvement over random forest and moved me into the top half of competitors.
By tuning the hyper-parameters of the gradient boosted model, I was able to improve the predictions to reach the top 40%.
