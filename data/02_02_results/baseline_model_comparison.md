# Baseline Model Comparison

---

## Methodology

- **Input**: 5 year steps of CO2 data
- **Output**: Forecast 1 year step
- **Forecasting Strategy for DL models**: Recursive taken to compare with ARIMA
- **Test Period**: 9 years

## RMSE Results by Model and Country

| Model   |   China |   India |   United States |
|:--------|--------:|--------:|----------------:|
| ARIMA   |  429.38 |   99.1  |          356.26 |
| LSTM    | 5430.47 | 1379.38 |          607.75 |
| Bi-LSTM | 5556.95 | 1551.54 |          569.43 |
| ED-LSTM | 6162.63 | 1629.54 |          243.62 |
| CNN     | 2699.29 |  491.65 |          622.25 |

## Best Model Per Country (by RMSE)

- **United States**: ED-LSTM (RMSE: 243.62, MASE: 0.9545)
- **China**: ARIMA (RMSE: 429.38, MASE: 1.4815)
- **India**: ARIMA (RMSE: 99.10, MASE: 0.5976)
