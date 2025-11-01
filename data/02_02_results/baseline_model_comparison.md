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
| LSTM    |  526.39 |  133.89 |          234.61 |
| Bi-LSTM |  541.55 |  132.13 |          244.77 |
| ED-LSTM |  518.92 |  131.33 |          237.92 |
| CNN     |  571.25 |  139.4  |          243.94 |

## Best Model Per Country (by RMSE)

- **United States**: ARIMA (RMSE: 232.40, MASE: 0.9175)
- **China**: ARIMA (RMSE: 287.36, MASE: 0.8804)
- **India**: ED-LSTM (RMSE: 131.33, MASE: 0.6357)
