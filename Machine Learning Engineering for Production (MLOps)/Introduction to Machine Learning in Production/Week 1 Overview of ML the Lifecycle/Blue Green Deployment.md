# Blue Green Deployment
Creado: 2022-10-22 16:36
Tags: #mlops #ml-project-lifecycle #deployment-stage #deploy-patterns #blue-green-deployment
Topic: [[Week 1 Overview of ML the Lifecycle]]

----
The way the blue green deployment is implemented is you would have an old prediction service may be running on some sort of service. You will then spin up a new prediction service, the green version, and you would have the router suddenly switch the traffic over from the old one to the new one. 

The advantage of a blue green deployment is that there's an easy way to enable rollback

## Referencias
[[Deployment Stage]]