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


Strava uses a Elastic Search / Logstash / Kibana (ELK) stack for centralized logging. Each Mesos Agent runs a Logspout container which pulls all logs from colocated containers and ships them to the ELK stack. Log messages are annotated with metadata including the Agent host, container ID, and Marathon app name.



###question to ask

Source Database:
1.	What is the size of the source database(Teradata)?
2.	How many source database/schemas and tables do they have?
3.	What kind of users, roles, and permissions do they have on the source database?
4.	How can source database be accessed (firewalls, tunnels…)?
5.	Does all the source data need to move once or incremental?
6.	Can the Client afford downtime? How much?
7.	Do they need the source database to stay alive after the migration? For how long?
8.	What is the current Management and Monitoring strategy? Tools used?
9.	What is the current Backup and Archival strategy? Tools used?
10.	How often the data is being refreshed in the source database?
11.	Is the source data shared with any other systems?
12.	What are the top challenges / pain points with current database setup? 
13.	What are the current DB drivers in use? –For Example: OCI, PRO*C, ODBC, OLE DB, JDBC, ADO, ADO.NET, others? 

Target Database:
1.	Is PostgreSQL (community Version) going to be the target database or other third party PostgreSQL databases like EnterpriseDB, CitusData, Postgres-XL, etc?
2.	Are there any requirements related to High Availability (HA)?
3.	What happens to client application/processes after the migration?
4.	What problems are the expected to be resolved from the migration?       
