# Sales-Forecasting

## Introduction
Sales forecasting is an essential activity for the day to day operations of a retailer. The product forecasts are taken into consideration by merchants for the purchase and 
allocation decisions. In addition, it is used for as an assortment optimization process for the stores to drive sales by catering to customer demands. By sales forecasting we get an idea which stores will need discounts and promotions
at what time during the year.

 ## Problem Statement
 The dataset is from a retail store that has multiple outlets across the country and  are facing issues in managing the inventory - to match the demand with 
 respect to supply. The task is to come up with useful insights using the data and make prediction models to forecast the sales for X number of months/years.
 
 ## Project Objective
 1.From the given dataset,we will come up  with useful insights that can be used by each of the stores to improve in various areas.
 2.Forecast the sales for each store for the next 12 weeks.
 
 ## Data Description
 The dataset contains 6435 records and 8 features. Holiday_flag gives information about holiday week.
 
 ## Data Pre-processing Steps and Inspiration
 We will check for missing values and found there are no missing values. There are 45 unique stores in the region hence each of these stores will have its own forecasting.
 In the notebook we have carried out sales forecasting for Store 10. The distribution of weekly sales is positively skewed. 
We see the weekly sales of the data across all the stores to get an idea.  Without considering holidays Store 4 has maximum weekly sales.When considering holiday we see Store 10 has maximum weekly sales followed by Store 20. 
The maximum weekly sales happens during the Christmas week(Week 51) which was  3818686.45.
From the average weekly sales graph for the stores it is clear that there is seasonality and no trend.
For seasonality it is clear that 1.Seasonality - High-Point: It seems there are some seasonality to our data, where the end of December seems like a popular time to buy specific products from the company. My assumptions is that this has to do with the holidays and people buy gifts for each other, which makes sense. 
2.Seasonality - Low-Point: Around the end of january it seems to be a pretty steep dip in the different stores sales both during 2011 and 2012.

## Choosing the algorithm.
As seen from the graphs, there is seasonality and we have to use past values to predict future values. 
# Model 1: Autoregressive Integrated Moving Average Model (ARIMA) 
An ARIMA model is a class of statistical models for analyzing and forecasting time series data.

It explicitly caters to a suite of standard structures in time series data, and as such provides a simple yet powerful method for making skillful time series forecasts.

ARIMA is an acronym that stands for AutoRegressive Integrated Moving Average. It is a generalization of the simpler AutoRegressive Moving Average and adds the notion of integration.
ARIMA models are generally denoted as ARIMA (p,d,q)  where p is the order of autoregressive model, d is the degree of differencing, and q is the order of moving-average model. 
ARIMA models use differencing to convert a non-stationary time series into a stationary one, and then predict future values from historical data. These models use “auto” correlations and moving averages over 
residual errors in the data to forecast future values.

In order to use time series forecasting models, we need to ensure that our time series data is stationary i.e constant mean, constant variance and constant covariance with time.

There are 2 ways to test the stationarity of time series:

a) Rolling Mean: A rolling analysis of a time series model is often used to assess the model’s stability over time. The window is rolled (slid across the data) on a weekly basis, in which the average is taken on a weekly basis. 
Rolling Mean is a visualization test, where we can compare the original data with the rolled data and check if the data is stationary or not.

b) Dicky -Fuller test: This test provides us the statistical data such as p-value to understand whether we can reject the null hypothesis. 
The null hypothesis is that data is not stationary and the alternative hypothesis says that data is stationary. 
If the p-value is less than the critical value (say 0.5), we will reject the null hypothesis and say that data is stationary.

# Model 2 : Prophet Model
Prophet is an open-source tool by Facebook. This procedure is used for forecasting time series data based on an additive model where non-linear trends are fit with yearly, weekly, and daily seasonality, plus holiday effects.

# Model 3 : XGBOOST
XGBoost stands for 'Extreme Gradient Boosting '.Boosting is an ensemble technique where new models are added to correct the errors made by existing models. Models are added sequentially until no further improvements can be made. A popular example is the AdaBoost algorithm that weights data points that are hard to predict.

Gradient boosting is an approach where new models are created that predict the residuals or errors of prior models and then added together to make the final prediction. It is called gradient boosting because it uses a gradient descent algorithm to minimize the loss when adding new models.

This approach supports both regression and classification predictive modeling problems.

## Motivations and Reasons for choosing the algorithm
As evident for time series SARIMA is most widely used algorithm. After applying the above three models, XGBOOST is the best performing model as RMSE is least for XGBoost.

##  Assumptions
For this dataset the assumptions are:
The assumptions are :
 1. All the stores are of same type and size.
 2. There are no departments in the store. A store is a single entity.
 
 ## Model Evaluation and Techniques
 There are two popular metrics used in measuring the performance of regression (continuous variable) models i.e MAE & RMSE.

Mean Absolute Error (MAE): It is the average of the absolute difference between the predicted values and observed values.

Root Mean Square Error (RMSE): It is the square root of the average of squared differences between the predicted values and observed values.

MAE is easier to understand and interpret but RMSE works well in situations where large errors are undesirable. This is because the errors are squared before they are averaged, thus penalizing large errors. 
In our case, RMSE suits well because we want to predict the sales with minimum error (i.e penalize high errors) so that inventory can be managed properly.

Hence we choose RMSE as a metric to measure the performance of our models.

## Inferences from the same
As we have choosen RMSE as our performance metric , it is evident from the RMSE values XGBoost is the best performing model for this dataset followed by SARIMA.

## Future possibilities of the project
The goal of sales forecasting is to accurately anticipate your sales performance. Sales professionals aim to either hit their expected target or, ideally, exceed it.

Sales forecasts help businesses make better decisions based on past performance  which will help them to:

-Forecast likely profit (or loss) in a designated period
-Organize staffing levels and create HR plans to be implemented
-Plan the required level of production needed to meet demand
-Gives sales leaders the right prospect and industry insights
-Helps sellers take the necessary steps toward continuous growth
-Sales forecasts often use historical data, industry trends, and the status of the current sales pipeline as benchmarks to estimate weekly, monthly, quarterly, and annual sales totals. 

It is imperative for sales team to use forecast as a baseline to work from, not view it as a set-in-stone certainty or goal. Sales forecasting is not to be confused with sales goal-setting. 
An organization sales goal outlines what you want to happen, while a sales forecast roughly estimates what might happen based on previous evidence or data – regardless
of your goal. 

Sales forecasting also helps in implementing promotional offers and discounts due certain times of the year to drive sales. A customized promotional offer for each store can help in achieving the target.

Please refer to Jupyter notebook to understand the implementation of the project.
