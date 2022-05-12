# Spark | The Definitive Guide

## Big Data Processing Made Simple

> Bill Chambers & Matei Zaharia

## Part I. Gentle Overview of Big Data and Spark

### Chapter 1. What is Apache Spark?

- Unified computing engine and set of libraries for parallel data processing on computer clusters.
- Currently moss actively developed open-source tool for this task
- Standard tool for any developer or data scientist using big data
- Supports multiple langueges
  - Python
  - Java
  - Scala
  - R
- Libraries for many tasks
  - SQL
  - Streaming
  - Machine learning
- Can run from a laptop to a cluster of thousands of servers

#### Apache  Spark's Philosophy

##### UNIFIED

- Wide range of analytics tasks (SQL to ML to streaming) over the same computing engine and with a consistent set of APIs
- Easier and more efficient to write

##### COMPUTING ENGINE

- Limited scope. 
- Handles loading dat from storage systems ad performing computations on it, not storage as an end in itself. 
- Use spark with range of other persistent storage systems
  - Cloud
    - Azure
    - Amazon S3
  - Distributed Systems
    - Apache Hadoop
  - key-value stores
    - Appache Cassandra
  - Message buses
    - Apache Kafka
- Most data exist in a mix of storage systems - Spark focuses on performing computations over the data no matter where it resides
  

##### LIBRARIES

- Unified APIs dor common data analysis tasks
- Supports standard and external, open-source libraries
- SparkSQL
- MLlib - Machine learning
- Stream Processing
- GraphX - Graph analytics
- [List of libraties](https://spark-packages.org/)

#### CONTEXT: The Big Data Problem

- Why do we need this?
- Most of history applications got bigger and faster over time running on single processors. Rate of processor improvement kept up with growing complexity.
- Trend stopped around 2005 due to physical limitation and focused on parallel processing using more CPU cores working together
- Applications needed to be optimized for parallelism to run faster
- Costs continue to go down and storage ability continue to go up
- Cost to store 1 TB of data halves every 14 months and sensors and other technology for capturing data also go down making it cheap to capture and store data

#### History of Spark

- UC BERkeley 2009
- MapReduce was dominant parallel programming enginefor clusters
- 2013 wide-spread use with over 100 contributors from more than 30 external organizations

#### Present and Future of Spark

- Continues to gain popularity and use
- Uber, Netflix, NASA, CERN

#### Running Spark

- Runs on Java virtual Machin (JVM)
  - Need an installation of Java
- Python interpreter
- Download and install apache spark on laptop
    - Install java any python first
    -  
1. Run Databricks COmmunity edition

-[ ] Come back to work on / troubleshoot install

### Chapter 2. A gentle introduction to Spark

- Application
- Core architecture of a cluster
- Spark Application
- Structured APIs
  - Datafames
  - SQL

#### Spark's Basic Architecture

- Computation on large amounts of data impossible on single machine - need cluster

#### Spark Applications

- Consist of a *driver* process and a set of *executor* processes
  - Driver runs `main()` function
    - Maintains information about the Spark Application
    - Responds to user input
    - Analyzes, distributes, and schedules work across the executors
  - Executors actually carries out work assigned by the driver
    - Executes code assigned
    - Reports state of computation on that executor back to driver node

#### Key Points

- Spark employs a cluster manager to keep track of the resources available
- Driver process is responsible for executing the driver program's commands across the executors to complete a given task

#### LAnguage APIs

- Python
- SQL
- Primarily written in Scala, making it spark's default languagge

#### Using spark

- Create SparkSession that manages Spark Application
- DataFrame - most common Structured API and simply represents a table of data with rows and columns
- Partitions - to allow every executor to work in parallel, spark breaks data into chunks called partitions - physically distributes data across clusters
- Transformations - core data structures are immutable, perform transformations instead
- Lazy evaluation - only calculates how to solve, doesn't do it until asked explicitly
- Run actions

---

# Learning Spark

## Lighting-fast data analytics

> Jules S. Damji, Brook Wenig, Tathagata Das, Denny Lee

## Chapter 1: Introduction to Apache Spark - A Unified Analytics Engine

- Unified engine for large-scale distributed data processing, on premises in data centers or in the cloud
- In-memory storage for intermediate computations
- Key characteristics
  - speed
    - Directed acyclic graph (DAG)
    - Scheduler and query optimizer
  - Ease of use
    - Resilient Distributed Dataser (RDD)
    - transformations and actions as operations
  - Modularity
    - Many supported languages
    - Many libraries
  - Extensibility
    - Decouples storage and processing
    - Can use many different sources

### Unified Analytics

- Spark SQL
  - Works well with structured data
  - Read data in an RMDBS table or from CSV, txt, JSON, Avro, ORC, Parquet, etc.
  - Construct permanent or temporary tables in Spark
  - Can read JSON, create a temp table, issue a SQL like query and read into memory as Spark Dataframe

### Spark MLlib

- Machine learning algorithms

## CH2 26-30)

### Spark Application Concepts

#### Application

- User program built on Spark using its APIs
- Consists of Driver program and executors n the cluster
- 

#### `SparkSessions`

- An abject that provides a point of entry to interact with underlying Spark functions
- Allows programming Spark with APIs
- Interactive spark shell, Spark driver instantiates `SparkSession` for you
- In a Spark application, you create the object yourself

#### Job

- Parallel computation consisting of multiple tasks that gets spawned in response to a Spark action (`save()`, `collect()`)

#### Stage

- Each job gets divided into smaller sets of tasks called stages that depend on each other
- ADG nodes - 


#### Task

- Sincle unit of work or execution that will be sent to a spark executor


#### Transformation, Actions, and Lazy Evaluation

- Transformations transform df into new df without altering the original dita, giving the property of immutability
- `select()`, `filter()` will not change the original DataFrame, but the transformed results
- Lazy evaluation - not computed immediately
- Actions trigger evaluation of all the recorded transformations
- Queries optimized peeking into chained transformations

| Transformation | Action      |
| -------------- | ----------- |
| `orderBy()`    | `show()`    |
| `groupBy`      | `take()`    |
| `filter()`     | `count()`   |
| `select()`     | `collect()` |
| `join()`       | `save()`    |

- Actions and transformation contribute to a spark query plan
- 