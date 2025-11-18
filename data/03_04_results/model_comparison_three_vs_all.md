# Model Performance Comparison: Target as Three Countries vs All Countries

- **Training Data**: All countries excluded regions and countries under 0.8 data coverage
## Average Performance Metrics

| Model | Avg RMSE (3 Countries) | Avg MASE (3 Countries) | Avg RMSE (All) | Avg MASE (All) |
|-------|------------------------|------------------------|----------------|----------------|
| LSTM | 209.7806 | 0.9145 | 8.8851 | 1.1815 |
| Bi-LSTM | 205.9044 | 0.8754 | 8.8768 | 1.1446 |
| ED-LSTM | 207.9348 | 0.8945 | 8.4789 | 1.0280 |
| CNN | 220.2112 | 0.9113 | 10.1876 | 1.2545 |
