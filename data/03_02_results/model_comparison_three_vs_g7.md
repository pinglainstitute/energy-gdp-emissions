# Model Performance Comparison: Target as Three Countries vs G7 Countries + China, India

- **Training Data**: All 9 G7 countries (US, China, India, Canada, France, Germany, Italy, Japan, UK)
## Average Performance Metrics

| Model | Avg RMSE (3 Countries) | Avg MASE (3 Countries) | Avg RMSE (G7) | Avg MASE (G7) |
|-------|------------------------|------------------------|---------------|---------------|
| RNN | 245.7524 | 0.9789 | 99.4686 | 1.0700 |
| LSTM | 223.0845 | 0.9102 | 90.7033 | 0.9686 |
| Bi-LSTM | 232.9156 | 0.9300 | 95.5960 | 1.0267 |
| ED-LSTM | 292.9165 | 1.1548 | 115.3541 | 1.0943 |
| CNN | 258.2622 | 0.9740 | 107.3599 | 1.1948 |
