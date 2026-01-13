# Model Performance Comparison: Target as Three Countries vs G7 Countries + China, India

- **Training Data**: All 9 G7 countries (US, China, India, Canada, France, Germany, Italy, Japan, UK)
## Average Performance Metrics

| Model | Avg RMSE (3 Countries) | Avg MASE (3 Countries) | Avg RMSE (G7) | Avg MASE (G7) |
|-------|------------------------|------------------------|---------------|---------------|
| RNN | 230.0038 | 0.9469 | 91.8960 | 0.9305 |
| LSTM | 228.1132 | 0.9129 | 93.1227 | 0.9910 |
| Bi-LSTM | 235.8312 | 0.9063 | 96.3121 | 1.0198 |
| ED-LSTM | 213.7827 | 0.9050 | 91.5689 | 1.1226 |
| CNN | 209.9881 | 0.8479 | 87.0538 | 0.9533 |
