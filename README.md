This project is only for learning purpose

Abstract:

In order to simulate the data streaming 
we created an endless loop that sample data from csv file 
send the data from one place to another (s3 bucket) 
by using (kafka) in (ec2) instance
then query above the data in the end with (amazon athena)

! this project inspired by youtuber DarshilParmar


After creating and setting up the EC2 instance in AWS
    
Open you terminal in your local machine and locate where your key value certification exist 

//connect to the instance using ssh

//install kafka

wget https://downloads.apache.org/kafka/3.8.0/kafka_2.12-3.8.0.tgz

tar -xvf kafka_2.12-3.8.0.tgz

//install openjdk

sudo yum install java-17-amazon-corretto-devel

cd kafka_2.12-3.8.0

//Start ZooKeeper

bin/zookeeper-server-start.sh config/zookeeper.properties

//Start KAFKA server
//before starting kafka server make sure that your instance in EC2 accessible from your local machine
//run "sudo nano config/server.properties" and add the public address of your ec2 instance in the ADVERTISED_LISTENERES
//now run the kafka server

bin/kafka-server-start.sh config/server.properties

//Create the topic
//open a new cmd , connect to the new cmd and locate to kafka repository in the instance

bin/kafka-topics.sh --create --topic topic_name --bootstrap-server youraddressippublic:9092 --replication-factor 1 --partitions 1

Now our Kafka and zookeeper is running and we created our topic

We gonna create our producer and consumer in the (Producer.ipnyb) and (Consumer.ipnyb) 

