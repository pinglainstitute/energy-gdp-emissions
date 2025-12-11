# Model Performance Comparison: Target as Three Countries vs G7 Countries + China, India

- **Training Data**: All 9 G7 countries (US, China, India, Canada, France, Germany, Italy, Japan, UK)
## Average Performance Metrics

| Model | Avg RMSE (3 Countries) | Avg MASE (3 Countries) | Avg RMSE (G7) | Avg MASE (G7) |
|-------|------------------------|------------------------|---------------|---------------|
| RNN | 253.3669 | 1.1148 | 109.7127 | 1.3390 |
| LSTM | 246.4614 | 0.9504 | 99.4562 | 1.0183 |
| Bi-LSTM | 239.7841 | 0.9491 | 97.1248 | 1.0015 |
| ED-LSTM | 626.8307 | 2.4714 | 234.5459 | 1.7725 |
| CNN | 214.0100 | 0.9203 | 95.9107 | 1.3251 |
