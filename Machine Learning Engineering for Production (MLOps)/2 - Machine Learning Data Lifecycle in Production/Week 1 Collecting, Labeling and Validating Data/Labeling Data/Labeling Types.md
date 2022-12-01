Creado: 2022-11-30 11:59
Tags: #mlops #data-lifecycle #labeling-data #labeling-types
Topic: [[Week 1 Collecting, Labeling and Validating Data]]

----

Labeling can be classified in different methods:
- Process Feedback (Direct Labeling):
	![[Pasted image 20221130171537.png]]
	- Advantages:
		- Training dataset continous creation
		- Labels evolve quickly
		- Capture strong label signals
	- Disavantages:
		- Hindered by inherent nature of the problem
		- Failure to capture ground truth
		- Largely bespoke design
	- Tools:
		- Lagstash, Fluentd
		- Google Clound Logging, AWS ElasticSearch, Azure Monitor
- Human Labeling: *People ("raters") to examine data and assign labels manually*
	- Methodology:
		- Unlabeled data is collected
		- Human "raters" are recruited
		- Instructions to guide raters are created
		- Data is divided and assigned to raters
		- Labels are collected and conflicts resolved
	- Advantages:
		- More labels
		- Pure supervised learning
	- Disadvantages:
		- Quality consitency: Many datasets difficult for human labeling
		- Slow
		- Expensive
		- Small Dataset Curation
- Semi Supervised Labeling
- Active Labeling
- Weak Supervision


## Referencias