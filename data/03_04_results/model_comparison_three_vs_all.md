# Model Performance Comparison: Target as Three Countries vs All Countries

- **Training Data**: All countries excluded regions and countries under 0.8 data coverage
## Average Performance Metrics

| Model | Avg RMSE (3 Countries) | Avg MASE (3 Countries) | Avg RMSE (All) | Avg MASE (All) |
|-------|------------------------|------------------------|----------------|----------------|
| RNN | 258.3217 | 1.0421 | 9.7187 | 1.1006 |
| LSTM | 209.7964 | 0.8875 | 8.7068 | 1.1439 |
| Bi-LSTM | 221.7724 | 1.0003 | 9.0177 | 1.1560 |
| ED-LSTM | 218.2304 | 0.8912 | 8.9124 | 1.0808 |
| CNN | 247.5820 | 0.9856 | 10.5282 | 1.2670 |
