# ARIMA Model Method Comparison

---

## Full Results by Country and Method

| Country       | Method               | Order     |      RMSE |       MAE |     BIC |
|:--------------|:---------------------|:----------|----------:|----------:|--------:|
| United States | Baseline (1,1,1)     | (1, 1, 1) |  368.395  |  298.165  | nan     |
| United States | Auto ARIMA (fixed d) | (0, 1, 0) |  356.259  |  286.951  | 574.158 |
| United States | Auto ARIMA (free d)  | (0, 1, 0) |  356.259  |  286.951  | 574.158 |
| United States | Manual Grid Search   | (2, 4, 2) |  557.711  |  392.192  | nan     |
| China         | Baseline (1,1,1)     | (1, 1, 1) |  497.839  |  426.659  | nan     |
| China         | Auto ARIMA (fixed d) | (0, 2, 0) |  429.382  |  372.257  | 572.211 |
| China         | Auto ARIMA (free d)  | (0, 2, 0) |  429.382  |  372.257  | 572.211 |
| China         | Manual Grid Search   | (2, 4, 2) | 2066.09   | 1926.98   | nan     |
| India         | Baseline (1,1,1)     | (1, 1, 1) |   99.1002 |   79.5966 | nan     |
| India         | Auto ARIMA (fixed d) | (0, 2, 1) |  107.012  |   83.4386 | 398.843 |
| India         | Auto ARIMA (free d)  | (0, 2, 1) |  107.012  |   83.4386 | 398.843 |
| India         | Manual Grid Search   | (2, 3, 1) |  172.808  |  116.128  | nan     |

## RMSE by Method (Averaged Across Countries)

| Method               |    mean |      std |
|:---------------------|--------:|---------:|
| Auto ARIMA (fixed d) | 297.551 |  169.013 |
| Auto ARIMA (free d)  | 297.551 |  169.013 |
| Baseline (1,1,1)     | 321.778 |  203.416 |
| Manual Grid Search   | 932.204 | 1000.66  |

## Best Performing Method Per Country

- **United States** : Auto ARIMA (fixed d) - Order (0, 1, 0), RMSE=356.2588
- **China** : Auto ARIMA (fixed d) - Order (0, 2, 0), RMSE=429.3823
- **India** : Baseline (1,1,1) - Order (1, 1, 1), RMSE=99.1002

