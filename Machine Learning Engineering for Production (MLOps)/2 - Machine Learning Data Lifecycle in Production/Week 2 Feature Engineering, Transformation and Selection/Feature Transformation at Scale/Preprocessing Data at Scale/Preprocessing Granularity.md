Creado: 2023-07-30 20:15
Tags: #mlops #feat-engineering #feat-transformation #preprocessing-granularity
Topic: [[Week 2 Feature Engineering, Transformation and Selection]]

----

There's a notion of the granularity at which you're doing preprocessing.

You're going to do transformations, both the instance level and a full pass over your data. And depending on the transformation that you're doing, you may be doing it in one or the other. You can usually always do instance level. But full path requires that you have the whole dataset.

| Instance Level     | Full-Pass        |
| ------------------ | ---------------- |
| Clipping           | Minimax          |
| Multiplying        | Standard scaling |
| Expanding features | Bucketizing      |
| etc.               | etc.                 |

## Referencias
[[Inconsistencies in Feature Engineering]]