## Traffic

The traffic example is an Envelope pipeline that retrieves measurements of traffic congestion and stores an aggregated view of the traffic congestion at a point in time using the current measurement and all of those in the previous 60 seconds. Within Envelope this uses the Apache Spark Streaming window operations functionality. This example demonstrates use cases that need to do live aggregations of recently received messages prior to user querying.

A sample configuration file is provided for reference. After creating the required Apache Kudu tables using the provided Apache Impala (incubating) scripts, the example can be run as:

    SPARK_KAFKA_VERSION=0.10 spark2-submit envelope-*.jar traffic.conf

An Apache Kafka producer to generate sample messages for the example, and push them in to the "traffic" topic, can be run as:

    spark2-submit --class com.cloudera.labs.envelope.examples.TrafficGenerator envelope-*.jar kafkabrokerhost:9092 traffic
    