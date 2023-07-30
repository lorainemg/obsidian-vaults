Creado: 2023-07-23 22:16
Tags: #mlops #feat-engineering #process-feat-eng
Topic: [[Week 2 Feature Engineering, Transformation and Selection]]

----
Feature engineering is usually applied in two ways:
- During training, you usually have the entire data set available to you, so you can use global properties of individual features in your feature engineering transformations. 
- During serving, you must do the same feature engineering so that you give your model the same types of data that it was trained on.

However, during training and serving, you typically process each request individually, so it's important that you include global properties of your features, such as the standard deviation. If you use it during training include that with the feature engineering that you do when serving, failing to do that right is a very common source of problems in production systems, and often these errors are difficult to find.

## Referencias
[[Art of Feature Engineering]]