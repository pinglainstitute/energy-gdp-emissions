# Baseline Model Comparison

---

## Methodology

- **Input**: 5 year steps of CO2 data
- **Output**: Forecast 1 year step
- **Normalisation**: DL models using pct change from the previous year normalisation, ARIMA with original values
- **Forecasting Strategy for DL models**: Single-step prediction for each time step
- **Test Period**: 9 years

## RMSE Results by Model and Country

| Model   |   China |   India |   United States |
|:--------|--------:|--------:|----------------:|
| ARIMA   |  287.36 |  160.46 |          232.4  |
| LSTM    |  329.05 |  128.5  |          274.44 |
| Bi-LSTM |  336.28 |  135.43 |          269.61 |
| ED-LSTM |  390.44 |  123.15 |          368.84 |
| CNN     |  338.61 |  145.98 |          277.43 |

## Best Model Per Country (by RMSE)

- **United States**: ARIMA (RMSE: 232.40, MASE: 0.9175)
- **China**: ARIMA (RMSE: 287.36, MASE: 0.8804)
- **India**: ED-LSTM (RMSE: 123.15, MASE: 0.6422)
