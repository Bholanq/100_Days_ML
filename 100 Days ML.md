Machine Learning is a field of computer science that uses **statistical techniques** to give computer systems the ability to "learn" with data, without being explicitly programmed.

![[Pasted image 20260410054430.png|264]]

## AI vs ML vs DL

DL - ML + Neurons Layers
In ML we have to specify the features ourselves but in DL, the systems picks up on the features themselves.

## Types of Machine Learning 
Based one the amount of supervision needed 4 types:

1. [[Supervised]] 
2. [[Unsupervised]]
3. [[Semi-supervised]]
4. [[Reinforcement learning]] 

## Batch vs Online Machine Learning 

|Feature|Batch Learning|Online Learning|
|---|---|---|
|Data Processing|All at once|One by one / small chunks|
|Updates|Retrain entire model|Incremental updates|
|Speed|Slow updates|Fast updates|
|Use Case|Static datasets|Streaming/real-time data|
|Memory Usage|High|Lower|
Batch - The entire data is used to train the model once. Usually offline. Then deployed.

Problem - If the data is updated then the entire Model has to retrained with the complete new data.

**Pros:**
- Good for large, static datasets
- Easier to debug and evaluate
- Often better performance after full training
**Cons:**
- Slow to update
- High compute cost for retraining
- Not suitable for real-time changes

Online - The model is trained then deployed. But unlike batch learning it dynamically keeps training with the new incremental data.

Pros: 
- Real-time updates
- Efficient for large/streaming data
- Adapts to changing patterns (concept drift)
Cons:
- Can be noisy/unstable - the libraries aren't enterprise grade.
- Harder to debug
- Risk of forgetting older patterns

**Out-of-Core Learning** - When the data is so large it can't be processed at once, so it broken down into smaller chunks then processed incrementally.

The data is broken down offline, but since it being fed incrementally its online learning.

![[Pasted image 20260411101144.png|278]]

## Instance vs Model Based Learning 

Memorization vs Generalization

Instance Based - The model **stores training data** and makes predictions by comparing new data to stored examples.

Pros:
- Not training phase, faster.
- Simple
Cons:
- Storage Heavy as we require all the training data.
- Not very scalable 
- Slow during predictions
Eg. KNN 
Model - The model **learns a function/pattern** from data and uses it for predictions.
Pros:
- Minimum storage requirement as we only need to store the function/rule. 
- More scalable.
Cons:
- Training phase may take time/costly.
- May underfit/overfit.
Eg. Logistic Regression, Linear R, Decision Trees etc.