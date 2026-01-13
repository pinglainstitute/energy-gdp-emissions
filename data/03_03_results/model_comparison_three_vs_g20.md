# Model Performance Comparison: Target as Three Countries vs G20 Countries

- **Training Data**: All G20 countries
## Average Performance Metrics

| Model | Avg RMSE (3 Countries) | Avg MASE (3 Countries) | Avg RMSE (G20) | Avg MASE (G20) |
|-------|------------------------|------------------------|----------------|----------------|
| RNN | 221.1746 | 0.8838 | 58.5711 | 1.0381 |
| LSTM | 214.9973 | 0.8635 | 56.4779 | 0.9927 |
| Bi-LSTM | 218.0051 | 0.8737 | 56.8420 | 1.0100 |
| ED-LSTM | 238.1269 | 0.9721 | 65.8045 | 1.3101 |
| CNN | 228.3099 | 0.9128 | 59.4255 | 1.0897 |
