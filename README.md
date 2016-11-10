# HiBench Suite [![Build Status](https://travis-ci.org/intel-hadoop/HiBench.svg?branch=master)](https://travis-ci.org/intel-hadoop/HiBench)
## The bigdata micro benchmark suite ##


* Current version: 6.0
* Homepage: https://github.com/intel-hadoop/HiBench
* To ask a question or report an issue, please use Github Issues
* Contents:
  1. Overview
  2. Getting Started
  3. Workloads
  4. Supported Releases

---
### OVERVIEW ###

HiBench is a big data benchmark suite that helps evaluate different big data frameworks in terms of speed, throughput and system resource utilizations. It contains a set of Hadoop, Spark and streaming workloads, including Sort, WordCount, TeraSort, Sleep, SQL, PageRank, Nutch indexing, Bayes, Kmeans, NWeight and enhanced DFSIO, etc. It also contains several streaming workloads for Spark Streaming, Flink, Storm and Gearpump.

### Getting Started ###
 * [Build HiBench](docs/build-hibench.md)
 * [Run HadoopBench](docs/run-hadoopbench.md)
 * [Run SparkBench](docs/run-sparkbench.md)
 * [Run StreamingBench](docs/run-streamingbench.md) (Spark streaming, Flink, Storm, Gearpump)

### Workloads ###

There are totally 17 workloads in HiBench. The workloads are divided into 6 categories which are micro, ml(machine learning), sql, graph, websearch and streaming.

  **Micro Bechmarks:**

1. Sort (sort)

    This workload sorts its *text* input data, which is generated using RandomTextWriter.

2. WordCount (wordcount)

    This workload counts the occurrence of each word in the input data, which are generated using RandomTextWriter. It is representative of another typical class of real world MapReduce jobs - extracting a small amount of interesting data from large data set.

3. TeraSort (terasort)

    TeraSort is a standard benchmark created by Jim Gray. Its input data is generated by Hadoop TeraGen example program.

4. Sleep (sleep)

    This workload sleep an amount of seconds in each task to test framework scheduler.

5. enhanced DFSIO (dfsioe)

    Enhanced DFSIO tests the HDFS throughput of the Hadoop cluster by generating a large number of tasks performing writes and reads simultaneously. It measures the average I/O rate of each map task, the average throughput of each map task, and the aggregated throughput of HDFS cluster. Note: this benchmark doesn't have Spark corresponding implementation.


**Machine Learning:**

1. Bayesian Classification (bayes)

    This workload benchmarks NaiveBayesian Classification implemented in Spark-MLLib/Mahout examples.

    Large-scale machine learning is another important use of MapReduce. This workload tests the Naive Bayesian (a popular classification algorithm for knowledge discovery and data mining)  trainer in Mahout 0.7, which is an open source (Apache project) machine learning library. The workload uses the automatically generated documents whose words follow the zipfian distribution. The dict used for text generation is also from the default linux file /usr/share/dict/linux.words.

2. K-means clustering (kmeans)

    This workload tests the K-means (a well-known clustering algorithm for knowledge discovery and data mining) clustering in Mahout 0.7/Spark-MLlib. The input data set is generated by GenKMeansDataset based on Uniform Distribution and Guassian Distribution.


**SQL:**

1. Scan (scan), Join(join), Aggregate(aggregation)

    These workloads are developed based on SIGMOD 09 paper "A Comparison of Approaches to Large-Scale Data Analysis" and HIVE-396. It contains Hive queries (Aggregation and Join) performing the typical OLAP queries described in the paper. Its input is also automatically generated Web data with hyperlinks following the Zipfian distribution.

**Websearch Benchmarks:**

1. PageRank (pagerank)

    This workload benchmarks PageRank algorithm implemented in Spark-MLLib/Hadoop (a search engine ranking benchmark included in pegasus 2.0) examples. The data source is generated from Web data whose hyperlinks follow the Zipfian distribution.

2. Nutch indexing (nutchindexing)

    Large-scale search indexing is one of the most significant uses of MapReduce. This workload tests the indexing sub-system in Nutch, a popular open source (Apache project) search engine. The workload uses the automatically generated Web data whose hyperlinks and words both follow the Zipfian distribution with corresponding parameters. The dict used to generate the Web page texts is the default linux dict file.

**Graph Benchmark:**

1. NWeight (nweight) 

    nweight.


**Streaming Benchmarks:**

1. Identity (identity)

    This workload reads input data from Kafka and then writes result to Kafka immediately, there is no complex business logic involved.

2. Repartition (repartition)

    This workload reads input data from Kafka and changes the level of parallelism by creating more or fewer partitionstests. It tests the efficiency of data shuffle in the streaming frameworks.
    
3. Stateful Wordcount (wordcount)

    This workload counts words cumulatively received from Kafka every few seconds. This tests the stateful operator performance and Checkpoint/Acker cost in the streaming frameworks.
    
4. Fixwindow (fixwindow)

    The workloads performs a window based aggregation. It tests the performance of window operation in the streaming frameworks.
  
    
### Supported Hadoop/Spark/Flink/Storm/Gearpump releases: ###

  - Hadoop: Apache Hadoop 2.x, CDH5, HDP
  - Spark: Spark 1.6.x, Spark 2.0.x
  - Flink: 1.0.3
  - Storm: 1.0.1
  - Gearpump: 0.8.1
  - Kafka: 0.8.2.2

---


