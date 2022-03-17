To test this project, launch 6 terminals:

# 1st Terminal for launching zookeper
zookeeper-server-start.sh /opt/kafka/config/zookeeper.properties

# 2nd Terminal for launching kafka
kafka-server-start.sh /opt/kafka/config/server.properties

# 3rd Terminal for launching the WordStream
mvn clean package
java -cp target/tp-kafka-0.0.1-SNAPSHOT.jar if4030.kafka.WordsStream

# 4th Terminal for launching the TaggedStream
java -cp target/tp-kafka-0.0.1-SNAPSHOT.jar if4030.kafka.TaggedStream 

# 5th Terminal for launching the consumer

## For the topic "words-stream" : 
kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic words-stream --formatter kafka.tools.DefaultMessageFormatter --property print.key=true --property key.deserializer=org.apache.kafka.common.serialization.StringDeserializer --property value.deserializer=org.apache.kafka.common.serialization.StringDeserializer

## For the topic "tagged-words-stream" :
kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic tagged-words-stream --formatter kafka.tools.DefaultMessageFormatter --property print.key=true --property key.deserializer=org.apache.kafka.common.serialization.StringDeserializer --property value.deserializer=org.apache.kafka.common.serialization.StringDeserializer

# 6th Terminal for the producer sending the book : 
cat book.txt | kafka-console-producer.sh --bootstrap-server localhost:9092         --topic lines-stream

You can then see the result on the 5th terminal


## Comments on the TP

I found it really hard to finish the TP and i was not able to finIsh with the 3rd component. 
There is very few documentation online and I spent literally about 20 hours on the project trying many things without mananaging to make it work... 
