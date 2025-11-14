# ARIMA Model Method Comparison

---

## Full Results by Country and Method

| Country       | Method               | Order     |      RMSE |       MAE |     BIC |
|:--------------|:---------------------|:----------|----------:|----------:|--------:|
| United States | Baseline (1,1,1)     | (1, 1, 1) |  368.395  |  298.165  | 577.213 |
| United States | Auto ARIMA (fixed d) | (0, 1, 0) |  356.259  |  286.951  | 574.158 |
| United States | Auto ARIMA (free d)  | (0, 1, 0) |  356.259  |  286.951  | 574.158 |
| United States | Manual Grid Search   | (2, 2, 0) |  226.796  |  158.133  | 569.289 |
| China         | Baseline (1,1,1)     | (1, 1, 1) |  497.839  |  426.659  | 587.9   |
| China         | Auto ARIMA (fixed d) | (0, 2, 0) |  429.382  |  372.257  | 572.211 |
| China         | Auto ARIMA (free d)  | (0, 2, 0) |  429.382  |  372.257  | 572.211 |
| China         | Manual Grid Search   | (2, 2, 0) | 1542.25   | 1474.88   | 571.423 |
| India         | Baseline (1,1,1)     | (1, 1, 1) |   99.1002 |   79.5966 | 414.079 |
| India         | Auto ARIMA (fixed d) | (0, 2, 1) |  107.012  |   83.4386 | 398.843 |
| India         | Auto ARIMA (free d)  | (0, 2, 1) |  107.012  |   83.4386 | 398.843 |
| India         | Manual Grid Search   | (2, 2, 0) |  120.618  |   84.7623 | 396.514 |

## RMSE by Method (Averaged Across Countries)

| Method               |    mean |     std |
|:---------------------|--------:|--------:|
| Auto ARIMA (fixed d) | 297.551 | 169.013 |
| Auto ARIMA (free d)  | 297.551 | 169.013 |
| Baseline (1,1,1)     | 321.778 | 203.416 |
| Manual Grid Search   | 629.89  | 791.913 |

## Best Performing Method Per Country

- **United States** : Manual Grid Search - Order (2, 2, 0), RMSE=226.7962
- **China** : Auto ARIMA (fixed d) - Order (0, 2, 0), RMSE=429.3823
- **India** : Baseline (1,1,1) - Order (1, 1, 1), RMSE=99.1002

