# Summary of Multivariate G7 DL models

RMSE of each DL model trained on G7 countries, China, and India combined dataset with selected features

The target countries are the US, China, and India

| Model   |    China |   India |   United States |
|:--------|---------:|--------:|----------------:|
| RNN     |  349.245 | 136     |         274.856 |
| LSTM    |  355.867 | 132.68  |         250.837 |
| Bi-LSTM |  332.439 | 130.682 |         256.231 |
| ED-LSTM | 1542.16  | 158.019 |         180.317 |
| CNN     |  235.38  | 149.599 |         257.051 |

---

MASE of each DL model trained on G7 countries, China, and India combined dataset with selected features

The target countries are the US, China, and India

| Model   |   China |   India |   United States |
|:--------|--------:|--------:|----------------:|
| RNN     |  1.1762 |  0.8505 |          1.3175 |
| LSTM    |  1.1216 |  0.7534 |          0.9762 |
| Bi-LSTM |  1.0737 |  0.7399 |          1.0337 |
| ED-LSTM |  5.8923 |  0.8613 |          0.6605 |
| CNN     |  0.7338 |  0.8625 |          1.1647 |

