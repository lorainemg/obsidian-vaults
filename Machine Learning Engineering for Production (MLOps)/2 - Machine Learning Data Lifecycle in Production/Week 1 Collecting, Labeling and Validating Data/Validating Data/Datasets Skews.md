Creado: 2022-12-03 13:24
Tags: #mlops #data-lifecycle #data-validation #data-skew
Topic: [[Week 1 Collecting, Labeling and Validating Data]]

----

- **Schema Skew**: Serving and training data don't conform to the same schema:
		- For example, `int != float`.
- **Feature Skew**: Training *feature values* are different than the serving *feature values*:
	- Features values are modified between training and serving time.
	- Transformation applied only in one of the two instances.
- **Distribution Skew**: *Distribution* of serving and training dataset is significantly different:
	- Faulty sampling methods during training.
	- Different data sources for training and serving data.
	- Trend, seasonality, changes in data over time. 

## Referencias
[[Drift and Skew Definition]]
[[Skew Detection Workflow]]
[[TFDV capabilities]]