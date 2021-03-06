# **Time Series ML with LSTM in Keras (TF 2.0)**

This small project is for learning time series ML using LSTM RNN implemented with Keras model. The current version is v2. https://github.com/frh2020/topics/blob/master/time_series/time_series_bjpm25_lstm_v2.ipynb

The models are modified from **Multivariate Time Series Forecasting with LSTMs in Keras** by **Dr Jason Brownlee**.  https://machinelearningmastery.com/multivariate-time-series-forecasting-lstms-keras/

The raw data file is a Beijing air quality dataset. the dataset was pre-processed a bit to be used in this work. https://github.com/frh2020/topics/blob/master/time_series/time_series_bjpm25_dp.ipynb

Multiple features and 5 years data (recorded every hour) are used as input to predict the PM2.5 of the next hour(s).

A **many-to-many** LSTM neural network (see the figure of an example below) is used for this multivariate and multi-step case.

<p align="center">
<img src="https://drive.google.com/uc?id=159QK2H7IM282u97kQRqmqNxQkVThdoIR" width="500" >
</p>
<br />

## Modification from the original work in v1

1.   One-hot encoding is implemented for 'wind direction'.
2.   'Hours' and 'day-of-year' features are added as seasonality factors
3.   Providing more multiple hours of input and output time steps.
4.   Make output features selectable, automatically drop unwanted

## Modification from v1

1.   Implement multiple output timestep at data prep
2.   Use many-to-many LSTM model with 2 stages
3.   Simplify inverse scaling for output features
4.   Change codes around for 'values' assignment to avoid re-run issue 
5.   More plots

## Conditions


*   Input timesteps = 12 hours
*   Pred timestep = 4 hour
*   Input features: pm2.5, dew, temp, press, wind speed, wind directions, rain, snow, doy, hour
*   Output features: pm2.5, temp
*   Train data duration: 4 years
*   Test data duration: 1 year
*   Neurons = 50
*   Return_sequences = **false**  for 1st stage, **Ture** for 2nd.

## Remarks
Tests show that pm2.5 rmse is not sensitive to neuron number in the range of 40-100, lag hours 12-48.

Other features also are not sensitive to neuron number 40-100 but improve as lag hours increase from 12-48.

Univariate and multivariate models have similar results.

Seasonality feature 'doy' plays a significant role in the training. It impacts highly seasonally dependent features such as temperature.

## Future works
Internal state depends on number of days

## Credit
Origianl work and referances are 

https://machinelearningmastery.com/multivariate-time-series-forecasting-lstms-keras/

https://machinelearningmastery.com/how-to-develop-lstm-models-for-time-series-forecasting/

https://machinelearningmastery.com/start-here/#deep_learning_time_series
