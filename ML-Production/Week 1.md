Example using Deployment example
Scratches on [phone ] detection in factory 
We have edge device in factory which checks if the image of the mobile and sends an api request to prediction server which predicts what decision to choose
Concept drift and data drift
ML production and POC to production gap
![[Pasted image 20230909123440.png]]
![[Pasted image 20230909123720.png]]

In speech recognition example
Defining dataa ther ecna be some inconsistencies when collecting the data so you should always use best practice like use some standard procedures to follow during your entire project.
How much silence before and after the speaker.
How do you perform volume normalisation

Modelling:
Code,Hyperparameters,Data 
![[Pasted image 20230909124402.png]]

Deployment
![[Pasted image 20230909124600.png]]


Challenges in Deployment 
Conceptual Drift and data drift
Training set: Historical Data
Test set: data from few months ago
How has the data change

Gradual change
Sudden shock: Examples like COVID 19 where people suddenly bought more things using credit cards.

Software engineering issues:
Prediction Service: 
Checklist of questions
Real-time or batch
Cloud or Edge/Browser
Compute resources(CPU/GPU/Memory)
Latency,throughput
Logging 
Security

First deployment is very different from maintenance

Common deployment cases
1) New product/capability
2) Automate with manual task
3) Replace previous ML system
Key ideas
1) Gradual ramp up with monitoring
2) Rollback

Visual inspection example
Shadow mode: using human for inspection as well as ml model
canary employment

Blue green deployment 
Easy way to enable rollback

All the degrees of automation
1) Human only
2) Shadow mode
3) AI assistance
4) Partial automation
5) Full automation

Monitoring dashboard
metrics to track examples
1) Software metrics
2) Input metrics
3) Output metrics

![[Pasted image 20230909203057.png]]


Deployment

Speech recognition example
Audio to speech recognition in edge devices VAD(Voice activity detection) is used.

