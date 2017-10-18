Spark memory setup for 100GB memory and 100 vCores
spark-shell \
--master yarn \
--deploy-mode client \ # change this to cluster
--driver-memory 5G \  
--executor-memory 3G \  # 3 per executor x num of exec 30 = 3 x 30 = 90GB
--num-executors 30 \
--driver-cores 10 \
--executor-cores 3 \   # 3 per exec   3 x 30 = 90 + 10 = 100
--packages org.mongodb.spark:mongo-spark-connector_2.11:2.1.0 \
--jars jars/report-1.0-SNAPSHOT.jar,jars/ojdbc7.jar \
--driver-class-path jars/ojdbc7.jar
