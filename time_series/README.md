# **Time Series ML with LSTM with Keras (TF 2.0)**

This notebook is for me practicing time series ML with LSTM and based on **Multivariate Time Series Forecasting with LSTMs in Keras** by **Dr Jason Brownlee** . The great original work is here https://machinelearningmastery.com/multivariate-time-series-forecasting-lstms-keras/


The raw data file is a Beijing air quality dataset. the dataset was pre-processed a bit to be used in this work.

a **many-to-many** LSTM model is used for this multivariate and multi-step case.

![many-to-many](https://drive.google.com/uc?id=1S-j9w6nYi9eVo0NJaQ4gTZx6JAQJtZeu)

## modification from the original work in v1

1.   One-hot encoding is implemented for 'wind direction'.
2.   'hours' and 'day-of-year' features are added as seasonality factors
3.   Providing more multiple hours of input and output time steps.
4.   make output features selectable, automatically drop unwanted

## modification from v1

1.   implement multiple output timestep at data prep
2.   use many-to-many LSTM model with 2 stages
3.   simplify inverse scaling for output features
4.   change codes around for 'values' assignment to avoid re-run issue 
5.   more plots

## conditions


*   input timesteps = 12 hours
*   pred timestep = 4 hour
*   input features: all
*   output features: pm2.5, temp, rain
*   train data duration: 4 years
*   test data duration: 1 year
*   neurons = 50
*   return_sequence = **false**  for 1st stage, **Ture** for output
