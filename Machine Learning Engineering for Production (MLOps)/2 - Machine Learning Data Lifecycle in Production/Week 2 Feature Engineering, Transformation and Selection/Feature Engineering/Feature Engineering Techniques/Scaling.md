Creado: 2023-07-23 23:31
Tags: #mlops #feat-engineering #feat-techniques #scaling
Topic: [[Week 2 Feature Engineering, Transformation and Selection]]

----
- Converts values from their natural range into a prescribed range.
	- E.g.: Grayscale image pixel intensity scale is [0, 255], usually scaled to [-1, 1]
- Benefits:
	- Helps neural nets converge faster
	- Do away with NaN errors during trainig
	- For each feature, the model learns the right weights.

## Referencias
[[Feature Engineering Techniques]]