Creado: 2022-12-03 12:37
Tags: #mlops #data-lifecycle #data-validation #distribution-skew
Topic: [[Week 1 Collecting, Labeling and Validating Data]]

----

### Probabilities of the Train and the Serve Datasets:
|             | Training         | Serving          |
| ----------- | ---------------- | ---------------- |
| Joint       | $P_{train}(y,x)$ | $P_{serve}(y,x)$ |
| Conditional | $P_{train}(y \vert x)$              | $P_{serve}(y \vert x)$ |
| Marginal    | $P_{train}(x)$            | $P_{serve}(x)$       |

#### Dataset Shift:
$$P_{train}(y,x) \neq P_{serve}(y,x)$$

#### Covariate Shift:
$$ P_{train}(y \vert x) = P_{serve}(y \vert x) $$
$$P_{train}(x) \neq P_{serve}(x)$$

#### Concept Shift:
$$P_{train}(y\vert x) \neq P_{serve}(y\vert x)$$
$$P_{train}(x) = P_{serve}(x)$$


## Referencias
[[Drift and Skew Definition]]
[[Detecting Data Issues]]