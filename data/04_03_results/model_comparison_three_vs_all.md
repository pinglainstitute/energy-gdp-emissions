# Model Performance Comparison: Target as Three Countries vs All Countries

- **Training Data**: All countries excluded regions and countries under 0.8 data coverage
## Average Performance Metrics

| Model | Avg RMSE (3 Countries) | Avg MASE (3 Countries) | Avg RMSE (All) | Avg MASE (All) |
|-------|------------------------|------------------------|----------------|----------------|
| RNN | 304.2160 | 1.2353 | 11.6289 | 1.3074 |
| LSTM | 240.1494 | 0.9639 | 9.1978 | 1.0714 |
| Bi-LSTM | 224.9377 | 0.9242 | 8.9625 | 1.0778 |
| ED-LSTM | 249.4375 | 0.9892 | 9.3691 | 1.0931 |
| CNN | 254.7868 | 1.0092 | 9.7573 | 1.1748 |
