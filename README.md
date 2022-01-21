# Kafka-Connect
This includes a tutorial to have kafka set up on a computer

**Installing Kafka**
-Clone down this repository to make file available for kafka set up 
-Kafka requires Java to run properly. Check to see if computer has java installed using command $ [java -version]()
- if java doesn't exist, use the following command to installjava in the system.
$ [brew install homebrew/cask/java]()
-verify installation with command: 
$ [brew cask info java]()

**Starting Zookeeper and Kafka Broker**
-Zookeeper is required to run Kafka, so Zookeeper needs to start first before running kakfa
-folder bin/ contains all executable files for MacOS and Ubuntu. 
-folder config/ contains default configurations for specific services that can be started using executable files from bin/

-Start Zookeeper (it is mandatory to run zookeeper before kafka broker)
$[bin/zookeeper-server-start.sh config/zookeeper.properties]()

-Start Kafka Broker (open new tab and type the following command. These two tabs need to be runnign for server to run)
$[bin/kafka-server-start.sh config/server.properties]()

**Create Kafka Topic and Explore Contents of the Topic**
-At this moment, Zookeeper is running on localhost:2181 and Kafka broker is running on localhost:9092

- In a new tab, create a Kafka topic using bin/kafka-topics. (creating a topic named test-1
$[bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1 --topic test1]()

- Read created topics by using the following commands
$[bin/kafka-topics.sh --list --bootstrap-server localhost:9092]()
$[bin/kafka-topics.sh --describe --bootstrap-server localhost:9092 --topic test1]()

**Creating Producers and Consumers**
- create a producer using the following command 
$ [bin/kafka-console-producer.sh --topic test1 --broker-list localhost:9092]()

- create a consumer using the following command:
$[bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test1]()
This one recieves messages sent live, but does not find all messages previously sent
$[bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test1 --from-beginning]()
















