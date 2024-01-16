---
layout: home
title: Kafka Quick Read
author: Kishore Kota

nav_order: 2
---


## Why I wrote this page ?

I alway feel TLDR, but I had to be little more patient than I was, and had to read through lots of doc from Apache Kafka and ChatGPT to have full understanding on Kafka. I hope this will help as a quick read into Kafka, what is it, use cases, how it works under the hood...so on.

I hope this blog helps you get to know some of the key details as a quick read. If it does, give me shout by liking my git repo.

## What is Kafka ?

Kafka is an Event Streaming processing infrastructure. It is designed to support high-throighput, low latency for handling real time data feeds. Kafka can support many different use cases for today data needs - it can vary from event driven systems to  real data streaming or data lake ingestion. These are supported by the following key capabilities.

- Ability to Pusblish and Consume.
- Store Streams of Events Durable and Realibly.
- Process Streams if Events as they occur or retrospectively.


## What are the main components in Kafka ?

- Controller
  * A Kafka controller is a broker that manages the states of partitions and replicas in a Kafka cluster. It also performs administrative tasks like reassigning partitions and maintains the consistency of replicas. 
  * KafkaController is a Kafka service that runs on every broker in a Kafka cluster. It is created and immediately started alongside KafkaServer.
- Broker
  * A Kafka broker is a server in a Kafka cluster that receives and sends data. It's also known as a bootstrap server because every broker has metadata about the other brokers and helps clients connect to them.
- Topic
  * A topic is a category feed that is used to organize published data. It must unique name in a given kafka Cluster.
- Partition
  * A partition is break down of the Kafka topic into groups which allow  parallel processing of Publishing and Consumption of the topic.
- Connector
  * A Connector is a component that can import or export data to and from external system into a Kafka Topic. It is classified into Source Connector and Sink Connector. A Source Connector is used to produce data into a topic from an external source. A Sink Connector is used to take data from a topic and send to a external source.
- Producer
  * Client application that is producing data into a Kafka Topic.
- Consumer
  * Client application that is consuming data from a Kafka Topic.



We will talk more details about these in the next section.

## Kafka Resource Quotas

Kafka Cluster has ability to enforce quitas on the rquest to control the broker resources used by client. Two types oif client quotas can be enforced by Kafka broker for each group of client sharing a quota:
- Network bankwidth quitas
  * Defines byte-rate thresholds.
- Request rate quitas
  * CPU Utlization threshotls as a percentage of network and I/O threads.