# Weekly Revenue Forecasting

## Project Overview  
The goal of this project was to build a machine learning pipeline to forecast weekly revenue for the next 12 weeks using historical data provided in a structured database. The dataset included weekly sales figures and metadata for three U.S. cities: Houston, San Francisco, and Spokane.

## Approach  
Each city was modeled separately to account for local dynamics and seasonality. Despite variations in absolute revenue and trends, the time series for all three cities followed similar patterns and were well-modeled using the same class of forecasting models.

Key steps included:

- Loading and cleaning the time series data for each city  
- Aggregating revenue at the weekly level  
- Checking for stationarity using the Augmented Dickey-Fuller test  
- Applying log transformation and differencing where appropriate  
- Fitting SARIMA and ARIMA models depending on seasonality and data availability  
- Generating 12-week forecasts and validating in-sample predictions

## Final Models  
Each city was best modeled using a version of ARIMA or SARIMA with:  
- Non-seasonal and seasonal moving average components  
- First differencing to achieve stationarity  
- Optional seasonal components (period=12) when the data length allowed for it  

The models demonstrated strong in-sample performance and produced consistent short-term forecasts that captured both level and trend.

## Notes  
- All modeling was done in Python using pandas, statsmodels, and matplotlib  
- Data was handled and visualized independently for each city  
- Forecasts were generated directly from the fitted models without manual reintegration or post-processing  
- Residuals were evaluated for autocorrelation and heteroskedasticity, with non-normality tolerated due to the nature of revenue data  
- Forecast outputs were prepared in both log and real revenue scales depending on the model pipeline  

## Next Steps  
To improve accuracy or adapt the models for production use, future enhancements could include:  
- Incorporating exogenous variables such as promotions, holidays, or weather  
- Automating model selection and tuning  
- Deploying a dashboard to visualize real-time forecasts and historical trends