-[batch and streaming 102](https://www.oreilly.com/ideas/the-world-beyond-batch-streaming-102)


###Spark vs Flink

Both tools are receiving wide adoption, with an edge to Spark for batch/bounded processing, and to Flink for 
streaming/unbounded processing (in particular, as Flink support native streaming and Spark relies on micro-batching, 
which incurs a latency penality that may inhibit some usecases). More conceptually, Flink is an explicit inheritor of 
Google's Dataflow (now rebranded Beam) model, whereas Spark's novelty comes from its resilient distributed datasets.



###### machine learning advice
However, the key piece of advice I'd give someone new to machine learning is not to get caught up in the different machine learning techniques (SVM vs random forrest vs neural network, etc). Instead (1) spend more time on translating your problem into terms a machine can understand (i.e how are you defining and generating your labels) and (2) how do you perform feature engineering so the the right variables are available for machine learning to use. Focusing on these two things helped me build more accurate models that were more likely to be deployed in the real world.
Feature engineering in particular has become a bit of a passion of mine since that realization. I currently work on an open source project called Featuretools (https://github.com/featuretools/featuretools/) that aims help people apply feature engineering to transactional or relational datasets. We just put out a tutorial on building models to predict what product a customer will buy next, which is a good hands on example to learn from https://github.com/featuretools/predict_next_purchase for beginners.


Docker:
Docker is a containerization tool. Containers function as lightweight and low overhead virtual machines. A Docker image is a file that forms the initial state of a container. It is immutable and carries no state, so containers run from the same image are initially identical.
Using containers allow developers to use whatever language or framework they wish. A service developer simply needs to produce a Docker image that implements their service. They don’t have to configure any servers.
