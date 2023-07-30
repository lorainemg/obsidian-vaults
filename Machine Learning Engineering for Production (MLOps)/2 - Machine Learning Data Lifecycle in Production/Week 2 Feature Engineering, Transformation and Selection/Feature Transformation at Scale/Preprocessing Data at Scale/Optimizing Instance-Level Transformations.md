Creado: 2023-07-30 20:15
Tags: #mlops #feat-engineering #feat-transformation #data-transforming #instance-level
Topic: [[Week 2 Feature Engineering, Transformation and Selection]]

----

### Problems:
- Indirectly affect training efficiency
- Typically accelators sit iddle while the CPU transform. That's something you might want to avoid because accelators are expensive.

### Solution:
- Prefetching transforms for better accelator efficiency.

## Referencias
[[Preprocessing Granularity]]