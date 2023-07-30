Creado: 2023-07-30 20:15
Tags: #mlops #feat-engineering #feat-transformation #preprocessing-inconsistencies 
Topic: [[Week 2 Feature Engineering, Transformation and Selection]]

----

Inconsitencies in feature engineering:
- Training & serving code paths are different (like using different code)
- Diverse deployment scenarios (you could use the same model in a servant cluster and on an IOT device). You need to think about what are the CPU resources or the compute resources that are available on those targets.
- Risks of introducing training-serving skews. That can happend if the same transformations are not used.
- Skews will lower the performance of your serving model.

## Referencias
[[Preprocessing Data at Scale Components]]