# The result of Baseline ARIMA for US, China, and India

Used features: `gdp`, `primary_energy_consumption`, `population`, `biofuel_share_energy`, `low_carbon_share_energy`, `methane`, `nitrous_oxide`

| country       | order     |   rmse_score |   mase_score |
|:--------------|:----------|-------------:|-------------:|
| United States | (1, 1, 1) |      368.395 |      2.29785 |
| China         | (0, 2, 2) |     1651.06  |      6.99193 |
| India         | (0, 2, 1) |      151.721 |      2.57844 |