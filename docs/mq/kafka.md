---
title: Kafka
hide:
  - tags

tags:
    - Kafka
    - Kafka Version History

---


# Kafka


---

## Kafka Version History

 
| Version  | Release Date   | Key Features Introduced                                                                       |
|----------|----------------|-----------------------------------------------------------------------------------------------|
| 0.8.0    | February 2013  | - Initial stable release<br>- Replication for fault tolerance<br>- New Producer API           |
| 1.0.0    | November 2017  | - Exactly Once Semantics (EOS)<br>- Performance enhancements<br>- Kafka Streams maturity      |
| 0.10.0.0 | May 2016       | - Introduction of Kafka Streams API for stream processing                                     |
| 1.1.0    | April 2018     | - Introduction of KSQL (now known as ksqlDB) for SQL-like stream processing                   |
| 2.6.0    | August 2020    | - KIP-500 early access to remove Zookeeper dependency<br>- Tiered storage for cost efficiency |
| 2.8.0    | April 2021     | - Continued work on KIP-500 for a simpler architecture without Zookeeper                      |
| 3.0.0    | September 2021 | -                                                                                             |
| 3.0.0    | September 2021 | -                                                                                             |
| 3.1.0    | January 2022   | -                                                                                             |
| 3.2.0    | May 2022       | -                                                                                             |
| 3.3.0    | 28 Sep 2022    | -                                                                                             |
| 3.4.0    | 06 Feb 2023    | -                                                                                             |
| 3.5.0    | 13 Jun 2023    | -                                                                                             |
| 3.6.0    | 03 Oct 2023    | -                                                                                             |


### Improvements and New Features

### 1. **Apache Kafka 3.0.0**:

#### **Major Improvements and New Features**:

  - **KRaft Consensus Mechanism**: Kafka 3.0 introduces improvements to **KRaft**, which is Kafka's built-in consensus mechanism designed to replace Apache ZooKeeper™. While KRaft is not yet recommended for production, enhancements have been made to its metadata and APIs.
 - **Exactly-Once Semantics**: Starting with Kafka 3.0, the producer now enables the **strongest delivery guarantees** by default (with `acks=all` and `enable.idempotence=true`). This ensures ordering and durability by default.
 - **Partition Reassignment Support**: Kafka Connect task restart enhancements, KStreams improvements in timestamp-based synchronization, and MirrorMaker2’s more flexible configuration options.

#### **Universal Changes**:

  - **Deprecation of Java 8**: Support for Java 8 is deprecated across all components of the Apache Kafka project in 3.0. Java 8 support is planned to be removed in the next major release (4.0).
  - **Deprecation of Scala 2.12**: Support for Scala 2.12 is also deprecated in Kafka 3.0, with plans to remove it in the next major release (4.0).

#### **KRaft Snapshot**:

 - KRaft controllers and brokers can now generate, replicate, and load snapshots for the metadata topic partition named `__cluster_metadata`. This efficient mechanism stores and replicates cluster metadata information.
    - **Revised KRaft Metadata Records**:
        - Improvements to metadata record types used when Kafka runs without ZooKeeper.
    - **Producer ID Generation in KRaft Mode**:
        - The Kafka Controller now fully handles generating producer IDs in both ZK and KRaft modes¹.

### 2. **Apache Kafka 3.6.0**:
 - **Many New Features and Improvements**:



---







