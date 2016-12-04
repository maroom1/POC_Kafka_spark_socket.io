# POC_Kafka_spark_socket.io

Dataset is at data/order_data

git clone https://github.com/maroom1/POC_Kafka_spark_socket.io.git

export PATH=$PATH:/usr/hdp/current/kafka-broker/bin kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic order-data

cd kafka

/bin/bash put_order_data_in_topic.sh ../data/order_data/ ip-172-31-13-154.ec2.internal:6667 order-data


export PATH=$PATH:/usr/hdp/current/kafka-broker/bin kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic order-one-min-data
 
 cd spark
 
 spark-submit --jars spark-streaming-kafka-assembly_2.10-1.6.0.jar spark_streaming_order_status.py localhost:2181 order-data

cd node

npm install

node index.js



 


