# Canary Deployment
Creado: 2022-10-22 16:31
Tags: #mlops #ml-project-lifecycle #deployment-stage #deploy-patterns #canary-deployment
Topic: [[Week 1 Overview of ML the Lifecycle]]

----

In the Canary Deployment pattern you would roll out to a small fraction, maybe 5%, maybe even less of traffic initially and start let the algorithm making real decisions. But by running this on only a small percentage of the traffic, hopefully, if the algorithm makes any mistakes it will affect only  a small fraction of the traffic. And this gives you more of an opportunity to monitor the system and ramp up the percentage of traffic it gets only gradually and only when you have greater confidence in this performance.

## Referencias
[[Deployment Stage]]