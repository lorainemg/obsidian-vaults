Creado: 2023-07-30 20:15
Tags: #mlops #feat-engineering #feat-transformation #data-transforming 
Topic: [[Week 2 Feature Engineering, Transformation and Selection]]

----

- Preprocessing training dataset:
	- Pros:
		- Run-once
		- Compute on entire dateset
	- Cons:
		- Transformations reproduced at serving
		- Slower iterations
- Transforming within the model:
	- Pros:
		- Easy iterations
		- Transformation guarantees
	- Cons:
		- Expensive transforms
		- Long model latency when serving the model
		- Transformations per batch: skew

## Referencias
[[Inconsistencies in Feature Engineering]]