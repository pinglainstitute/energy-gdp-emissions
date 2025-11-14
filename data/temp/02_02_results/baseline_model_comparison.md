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
| ARIMA   |  287.36 |  139.92 |          232.4  |
| LSTM    |  329.59 |  133.38 |          287.33 |
| Bi-LSTM |  318.81 |  133.87 |          279.53 |
| ED-LSTM |  390.1  |  123.14 |          368.66 |
| CNN     |  408.58 |  154.58 |          265.4  |

## Best Model Per Country (by RMSE)

- **United States**: ARIMA (RMSE: 232.40, MASE: 0.9175)
- **China**: ARIMA (RMSE: 287.36, MASE: 0.8804)
- **India**: ED-LSTM (RMSE: 123.14, MASE: 0.6423)
