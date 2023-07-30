Creado: 2023-07-30 20:15
Tags: #mlops #feat-engineering #feat-transformation #data-transforming #batch
Topic: [[Week 2 Feature Engineering, Transformation and Selection]]

----

You can transform per batch instead of for the entire dataset:
- For example, normalizing features by their average
- Access to a single batch of data, not the full dataset.
- There's ways to normalize per batch. That can be good in some cases, for example in time series, where you have changes over time.
	- Nomalize by average within the batch
	- Precompute averages and reuse it during normalization.

## Referencias
[[When to Transform]]