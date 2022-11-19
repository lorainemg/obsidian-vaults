Creado: 2022-11-19 18:14
Tags: #mlops #data-lifecycle #mlops-introduction #tfx
Topic: [[Week 1 Collecting, Labeling and Validating Data]]

----

TFX Production Components are:
| Steps               | Libraries                  | Components                                  | Explanation                                                                                                                                                                                         |
| ------------------- | -------------------------- | ------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Data Ingestion      | Data Ingestion             | ExampleGen                                  | Used to ingest our data                                                                                                                                                                             |
| Data Validation     | Tensorflow Data Validation | StatisticsGen, SchemaGen, Example Validator | StatisticsGen is used to generate statistics of our data.Example Validator is used to look for problems in our data. SchemaGen is used to generate a schema for our data across our feature vector. |
| Feature Engineering | Tensorflow Transform       | Transform                                   | Transform will do feature engineering.                                                                                                                                                              |
| Train Model         | Estimator or Keras Model   | Tuner and Trainer                           | Are used to train a model and to tune the hyper-parameters for that model.                                                                                                                          |
| Validate Model      | Tensorflow Model Analysis  | Evaluator                                   | Is used to do deep analysis of the performance of our model.                                                                                                                                        |
| Push if Good        | Validation Outcomes        | InfraValidator, Pusher                      | Infra Validator is used to make sure that we can actually run predictions using our model on the infrastructure that we have. Then Pusher pushes the model to Production.                           |
| Serve Model         | Tensorflow Serving         | Model Server, Bulk Inference                | -                                                                                                                                                                                                    |

## Referencias
[[TFX]]