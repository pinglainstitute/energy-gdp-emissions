# Model Performance Comparison: Target as Three Countries vs All Countries

- **Training Data**: All countries excluded regions and countries under 0.8 data coverage
## Average Performance Metrics

| Model | Avg RMSE (3 Countries) | Avg MASE (3 Countries) | Avg RMSE (All) | Avg MASE (All) |
|-------|------------------------|------------------------|----------------|----------------|
| RNN | 248.4592 | 1.0251 | 10.1309 | 1.1845 |
| LSTM | 220.6008 | 0.8959 | 9.1363 | 1.1692 |
| Bi-LSTM | 216.8545 | 0.9188 | 9.0323 | 1.2019 |
| ED-LSTM | 250.2924 | 1.0084 | 10.1412 | 1.1847 |
| CNN | 234.2697 | 0.9318 | 11.4309 | 1.4959 |
