# Model Performance Comparison: Target as Three Countries vs G7 Countries + China, India

- **Training Data**: All 9 G7 countries (US, China, India, Canada, France, Germany, Italy, Japan, UK)
## Average Performance Metrics

| Model | Avg RMSE (3 Countries) | Avg MASE (3 Countries) | Avg RMSE (G7) | Avg MASE (G7) |
|-------|------------------------|------------------------|---------------|---------------|
| RNN | 230.0038 | 0.9469 | 91.8960 | 0.9305 |
| LSTM | 228.1132 | 0.9129 | 93.1227 | 0.9910 |
| Bi-LSTM | 235.8312 | 0.9063 | 96.3121 | 1.0198 |
| ED-LSTM | 227.3559 | 0.9283 | 95.4515 | 1.1080 |
| CNN | 250.5639 | 1.0357 | 103.8922 | 1.1585 |
