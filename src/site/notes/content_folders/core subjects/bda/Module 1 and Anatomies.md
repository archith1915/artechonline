---
{"dg-publish":true,"permalink":"/content-folders/core-subjects/bda/module-1-and-anatomies/","dgShowToc":true}
---

# 5 Vs

Big Data refers to large, complex, and rapidly growing data sets that cannot be efficiently managed or analyzed using traditional data processing tools. To understand its characteristics, we describe it through **five dimensions**, known as the **5 Vs**:

---

### 1. Volume

- **Definition:**  
    Volume refers to the **size or quantity** of data generated, stored, and processed.  
    Big Data involves data sets ranging from **terabytes (TB)** to **petabytes (PB)** or even **zettabytes (ZB)**.
    
- **Explanation:**  
    Traditional databases cannot handle such massive quantities. Big Data technologies like **Hadoop** and **Spark** are used to store and process these volumes across distributed systems.
    
- **Example:**
    
    - Facebook generates **over 4 petabytes of data** daily (photos, videos, comments).
        
    - Sensors in a Boeing aircraft can produce **hundreds of terabytes** of flight data per trip.

---

### 2. Velocity

- **Definition:**  
    Velocity represents the **rate at which data is produced and moves** through systems for storage and analysis.
    
- **Explanation:**  
    Data is generated continuously and often needs **real-time** or **near real-time** processing to be useful. High velocity requires streaming technologies like **Apache Kafka**, **Apache Flink**, or **Spark Streaming**.
    
- **Example:**
    
    - Financial trading systems analyze **stock prices** in milliseconds.
        
    - Social media platforms process **millions of messages and reactions per second**.
        
    - IoT sensors in smart cities transmit live data on **traffic and pollution**.

---

### 3. Variety

- **Definition:**  
    Variety describes the **different forms and sources** of data being collected.
    
- **Explanation:**  
    Data is no longer just structured (rows and columns in a database). It includes **semi-structured** and **unstructured** formats like text, audio, video, images, and sensor data. Managing and integrating such diverse data requires flexible storage models such as **NoSQL databases** (MongoDB, Cassandra).
    
- **Example:**
    
    - E-commerce data includes **transaction records (structured)**, **customer reviews (text)**, **images**, and **clickstream logs**.
        
    - Healthcare systems handle **patient records**, **MRI scans**, and **genetic data**.

---

### 4. Veracity

- **Definition:**  
    Veracity refers to the **accuracy, reliability, and consistency** of data.
    
- **Explanation:**  
    Big Data comes from multiple, uncontrolled sources — which may include **incomplete, inconsistent, or noisy** information. Ensuring high veracity requires **data cleaning**, **validation**, and **filtering** techniques to eliminate errors and biases.
    
- **Example:**
    
    - On social media, fake news or spam posts affect the **reliability** of insights.
        
    - In healthcare, **faulty sensors** may provide inaccurate readings, leading to wrong analysis.

---

### 5. Value

- **Definition:**  
    Value represents the **business benefit or actionable insight** derived from analyzing Big Data.
    
- **Explanation:**  
    Collecting data is meaningless unless it produces value — such as improving decision-making, predicting trends, or optimizing operations. Big Data analytics tools like **Hadoop**, **Spark**, and **Tableau** help extract valuable patterns and intelligence.
    
- **Example:**
    
    - Netflix analyzes viewing patterns to **recommend shows** and **improve customer retention**.
        
    - Retailers use purchase history to **predict customer demand** and manage inventory efficiently.

---

## **Summary Table**

|**V**|**Meaning**|**Focus**|**Example**|
|---|---|---|---|
|**Volume**|Amount of data|Scale of data|Facebook data generation|
|**Velocity**|Speed of data generation/processing|Real-time streaming|Stock trading systems|
|**Variety**|Different data types/sources|Structured, unstructured, semi-structured|Text, video, sensor data|
|**Veracity**|Trustworthiness of data|Data quality and accuracy|Removing fake social media data|
|**Value**|Usefulness of data|Business insights and decisions|Netflix recommendations|

# SQL vs NoSQL

| **Feature**                         | **SQL Database**                                                                                                                  | **NoSQL Database**                                                                                                        |
| ----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| **1. Data Model**                   | Follows a **relational model** — data is stored in tables with rows and columns.                                                  | Follows a **non-relational model** — data can be stored as key-value pairs, documents, graphs, or wide-columns.           |
| **2. Schema**                       | Has a **fixed schema**. Structure (columns, data types) must be defined before inserting data.                                    | **Dynamic or flexible schema.** Data structure can change anytime without affecting existing data.                        |
| **3. Query Language**               | Uses **Structured Query Language (SQL)** for defining and manipulating data.                                                      | Uses **unstructured queries**, often specific to the database type (e.g., JSON queries, APIs).                            |
| **4. Scalability**                  | **Vertically scalable** — performance increases by upgrading hardware (CPU, RAM).                                                 | **Horizontally scalable** — performance increases by adding more servers (nodes).                                         |
| **5. Transactions**                 | Supports **ACID (Atomicity, Consistency, Isolation, Durability)** properties — ideal for applications requiring high consistency. | Often follows **BASE (Basically Available, Soft-state, Eventually consistent)** — focuses on scalability and flexibility. |
| **6. Storage Type**                 | Stores **structured data**.                                                                                                       | Handles **unstructured, semi-structured, and structured data**.                                                           |
| **7. Examples**                     | MySQL, PostgreSQL, Oracle, SQL Server.                                                                                            | MongoDB, Cassandra, Redis, CouchDB, Neo4j.                                                                                |
| **8. Best Suited For**              | Applications requiring complex queries and transactions — e.g., **banking systems, ERP, inventory management**.                   | Applications with rapidly changing data or large-scale storage — e.g., **social media, IoT, real-time analytics**.        |
| **9. Joins**                        | Supports **joins** to relate multiple tables.                                                                                     | Generally **does not support joins**; data is often stored together (denormalized).                                       |
| **10. Consistency vs Availability** | Prioritizes **consistency** over availability.                                                                                    | Prioritizes **availability and partition tolerance** (as per CAP theorem).                                                |
# Hive vs RDMBS

| **No.** | **Hive**                                                                                                              | **RDBMS**                                                                                    |
| :-----: | :-------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------- |
|  **1**  | Hive is a **data warehouse tool** built on top of Hadoop for analyzing large volumes of data.                         | RDBMS is a **database management system** used to store and manage structured data.          |
|  **2**  | Hive is designed for **batch processing** — processes large data in one go.                                           | RDBMS is designed for **transactional processing** — handles frequent read/write operations. |
|  **3**  | Hive uses **HiveQL**, a SQL-like query language that converts queries into **MapReduce/Spark jobs**.                  | RDBMS uses **SQL**, and queries run directly on the database engine.                         |
|  **4**  | Works on **HDFS (Hadoop Distributed File System)** — stores data in distributed form.                                 | Stores data on a **single centralized server** or limited cluster.                           |
|  **5**  | Supports **structured, semi-structured, and unstructured** data.                                                      | Supports only **structured** data with fixed schema.                                         |
|  **6**  | Follows **Schema-on-Read** — data schema applied when reading data.                                                   | Follows **Schema-on-Write** — data must match schema before writing.                         |
|  **7**  | Not suitable for **real-time updates or OLTP** (Online Transaction Processing).                                       | Highly suitable for **OLTP**, supporting updates, deletes, and inserts.                      |
|  **8**  | Provides **high scalability** — can easily scale horizontally by adding more nodes.                                   | Scales **vertically** — by upgrading CPU, RAM, or storage.                                   |
|  **9**  | Query results may take longer (since it runs distributed jobs), but it can handle **terabytes or petabytes of data**. | Query results are fast for small data, but performance drops for **very large datasets**.    |
| **10**  | Commonly used for **data analysis, reporting, and big data analytics**.                                               | Commonly used for **transactional systems** like banking or inventory databases.             |

# Hadoop vs RDBMS

|**No.**|**HADOOP**|**RDBMS**|
|:-:|:--|:--|
|**1**|Hadoop is a **framework** used for **distributed storage and parallel processing** of large datasets.|RDBMS is a **database management system** used to **store and manage structured data**.|
|**2**|Designed for **batch processing** of **Big Data**.|Designed for **real-time transaction processing** (OLTP).|
|**3**|Uses **HDFS (Hadoop Distributed File System)** to store data across multiple machines.|Stores data in a **centralized database** on a single server or small cluster.|
|**4**|Can process **structured, semi-structured, and unstructured** data.|Handles **only structured** data stored in relational tables.|
|**5**|Follows **Schema-on-Read** — data schema applied when data is read.|Follows **Schema-on-Write** — data must match schema before being written.|
|**6**|Does **not support real-time updates, inserts, or deletes**.|Supports **real-time insert, update, and delete** operations.|
|**7**|Provides **horizontal scalability** — can add more nodes easily to increase capacity.|Provides **vertical scalability** — needs more powerful hardware to scale.|
|**8**|Processes data using **MapReduce**, **YARN**, or **Spark**.|Processes data using a **database engine** with SQL queries.|
|**9**|Best suited for **data analysis, big data analytics, and batch processing** tasks.|Best suited for **transactional systems** like banking, inventory, or payroll.|
|**10**|Works efficiently on **commodity (low-cost) hardware**.|Requires **high-end hardware** for performance and reliability.|
|**11**|Offers **fault tolerance** — data is replicated across nodes to avoid loss.|Typically has **limited fault tolerance** unless configured with backups.|
|**12**|Open-source ecosystem including Hive, Pig, Spark, HBase, etc.|Usually commercial systems like Oracle, MySQL, SQL Server, etc.|

# Hive vs HBase

| **No.** | **HIVE**                                                                                                          | **HBASE**                                                                                             |
| :-----: | :---------------------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------- |
|  **1**  | Hive is a **data warehouse tool** built on top of Hadoop for **batch processing and analysis** of large datasets. | HBase is a **NoSQL database** built on top of Hadoop for **real-time read/write access** to big data. |
|  **2**  | Designed for **data analysis and querying** using **HiveQL** (SQL-like language).                                 | Designed for **fast data retrieval and updates** using **key-value pairs**.                           |
|  **3**  | Works on top of **HDFS** and processes data using **MapReduce or Tez/Spark**.                                     | Also works on **HDFS**, but provides **real-time random read/write** access instead of batch jobs.    |
|  **4**  | Follows **Schema-on-Read** — schema applied when data is queried.                                                 | Follows **Schema-on-Write** — data model (tables, column families) defined before storing.            |
|  **5**  | Best suited for **batch processing** — analyzing and summarizing massive data.                                    | Best suited for **real-time operations** — fetching or updating specific records quickly.             |
|  **6**  | Query language is **HiveQL**, similar to SQL.                                                                     | Query access is **NoSQL API-based** — uses Java or REST API, not SQL.                                 |
|  **7**  | Data is stored in **tables managed by Hive Metastore**.                                                           | Data is stored in **tables with rows and column families**, similar to Google Bigtable.               |
|  **8**  | **Latency is high** — queries take time to execute as they run distributed jobs.                                  | **Latency is low** — supports millisecond-level data access.                                          |
|  **9**  | Used for **data analysis, reporting, and summarization**.                                                         | Used for **real-time applications** like messaging, sensor data, and log updates.                     |
| **10**  | Not suitable for **real-time inserts or updates**.                                                                | Supports **real-time read/write** of millions of records per second.                                  |
| **11**  | Provides a **high-level abstraction** for querying data.                                                          | Provides a **low-level storage mechanism** for handling large datasets.                               |
| **12**  | Ideal for **batch analytics** and **ETL (Extract-Transform-Load)** operations.                                    | Ideal for **OLTP (Online Transaction Processing)** scenarios in big data systems.                     |

# Hive vs Pig

| **No.** | **HIVE**                                                                                      | **PIG**                                                                                    |
| :-----: | :-------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------- |
|  **1**  | Hive is a **data warehouse tool** built on Hadoop for **batch processing and data analysis**. | Pig is a **data flow scripting platform** used for **data processing and transformation**. |
|  **2**  | Designed mainly for **data querying and reporting**.                                          | Designed mainly for **ETL (Extract, Transform, Load)** operations.                         |
|  **3**  | Uses **HiveQL**, a **SQL-like query language**.                                               | Uses **Pig Latin**, a **procedural scripting language**.                                   |
|  **4**  | Suitable for users with **SQL knowledge**.                                                    | Suitable for **programmers and data engineers**.                                           |
|  **5**  | Works on top of **HDFS** and executes queries using **MapReduce / Tez / Spark**.              | Works on **HDFS** and converts Pig Latin scripts into **MapReduce jobs**.                  |
|  **6**  | Follows **Schema-on-Read** — schema is applied when querying data.                            | Also follows **Schema-on-Read**.                                                           |
|  **7**  | Best suited for **structured data** and tabular format.                                       | Handles **structured, semi-structured, and unstructured** data efficiently.                |
|  **8**  | Queries are **declarative** — user specifies _what_ to compute.                               | Scripts are **procedural** — user specifies _how_ to compute.                              |
|  **9**  | **High latency** — mainly for batch analytics, not real-time processing.                      | Also **high latency**, mainly for batch processing.                                        |
| **10**  | Commonly used for **data analysis, reporting, and summarization**.                            | Commonly used for **data cleansing, transformation, and preparation**.                     |
| **11**  | Provides a **higher-level abstraction** for querying data.                                    | Provides **lower-level control** over data processing steps.                               |
| **12**  | Easier to learn for **non-programmers**.                                                      | Requires some **programming knowledge**.                                                   |
# Pig vs Hive vs Spark

| **No.** | **PIG**                                                                  | **HIVE**                                                                  | **SPARK**                                                                                    |
| :-----: | :----------------------------------------------------------------------- | :------------------------------------------------------------------------ | :------------------------------------------------------------------------------------------- |
|  **1**  | Pig is a **data flow scripting platform** for processing large datasets. | Hive is a **data warehouse tool** for querying and analyzing big data.    | Spark is a **fast, in-memory distributed computing framework**.                              |
|  **2**  | Mainly used for **ETL (Extract, Transform, Load)** operations.           | Mainly used for **data analysis and reporting**.                          | Used for **data processing, analytics, and real-time computation**.                          |
|  **3**  | Uses **Pig Latin**, a **procedural scripting language**.                 | Uses **HiveQL**, a **SQL-like declarative language**.                     | Uses APIs in **Scala, Java, Python, and SQL (Spark SQL)**.                                   |
|  **4**  | Suitable for **programmers and data engineers**.                         | Suitable for users with **SQL background**.                               | Suitable for **data engineers, data scientists, and developers**.                            |
|  **5**  | Works on **HDFS** and executes scripts as **MapReduce jobs**.            | Works on **HDFS** and executes queries using **MapReduce / Tez / Spark**. | Works on **HDFS, HBase, cloud storage**, and processes data using **in-memory computation**. |
|  **6**  | Follows **Schema-on-Read**.                                              | Follows **Schema-on-Read**.                                               | Supports **Schema-on-Read** and structured processing via Spark SQL.                         |
|  **7**  | Best suited for **semi-structured and unstructured data**.               | Best suited for **structured data** in tabular format.                    | Supports **structured, semi-structured, and unstructured data**.                             |
|  **8**  | Processing is **batch-oriented** with **high latency**.                  | Processing is **batch-oriented** with **high latency**.                   | Supports **batch, streaming, and real-time processing** with **low latency**.                |
|  **9**  | Provides **lower-level control** over data processing steps.             | Provides **high-level abstraction** for querying data.                    | Provides **high-performance computing** with advanced APIs.                                  |
| **10**  | Not suitable for **real-time processing**.                               | Not suitable for **real-time processing**.                                | Highly suitable for **real-time analytics and streaming**.                                   |
| **11**  | Used for **data cleansing and transformation**.                          | Used for **data summarization and reporting**.                            | Used for **machine learning, streaming, graph processing, and analytics**.                   |
| **12**  | Slower due to **disk-based MapReduce execution**.                        | Slower due to **job-based execution model**.                              | Faster due to **in-memory execution**.                                                       |

# Anatomy of read/write 

## Anatomy of file read

![Pasted image 20251010195158.png](/img/user/Pasted%20image%2020251010195158.png)


### The steps involved in the File Read are as follows:

1. The client opens the file that it wishes to read from by calling open() on the DistributedFileSystem.
2. Distributed File System communicates with the NameNode to get the location of data blocks.  NameNode returns with the addresses of the DataNodes that the data blocks are stored on. Subsequent to this, the DistributedFileSystem returns an FSDatalnputStream to client to read from the file.
3. Client then calls read() on the stream DFSInputStream, which has addresses of the DataNodes for the first few blocks of the file, connects to the closest DataNode for the first block in the file.
4. Client calls read() repeatedly to stream the data from the DataNode.
5. When end of the block is reached, DFSInputStream closes the connection with the DataNode. It repeats the steps to find the best DataNode for the next block and subsequent blocks.
6. When the client completes the reading of the file, it calls close() on the FSDatalnputStream to close the connection.

## Anatomy of file write

![Pasted image 20251010210109.png](/img/user/Pasted%20image%2020251010210109.png)


### The steps involved in the File Write are as follows:


1. The client calls create() on DistributedFileSystem to create a file.  
2. An RPC call to the NameNode happens through the DistributedFileSystem to create a new file.The NameNode performs various checks to create a new file (checks whether such a file exists or not). Initially, the Name Node creates a file without associating any data blocks to the file. The DistributedFileSystem returns an FSDataOutputStream to the client to perform write.
3. As the client writes data, data is split into packets by DFSOutputStram, which is then written to internal queue, called data queue. DataStreamer consumes the data queue. The DataStreamer requests the NameNode to allocate new blocks by selecting a list of suitable DataNodes to store replicas. This list of DataNodes makes a pipeline. Here, we will go with the default replication factor of three, so there will be three nodes in the pipeline for the first block.
4. DataStreamer streams the packets to the first DataNode in the pipeline. It stores packet and forwards it to the second DataNode in the pipeline. In the same way, the second DataNode stores the packet and forwards it to the third DataNode in the pipeline.
5. In addition to the internal queue, DFSOutputStream also manages an "Ack queue" of packets that are waiting for the acknowledgement by DataNodes. A packet is removed from the "Ack queue" only if it is acknowledged by all the DataNodes in the pipeline.
6. When the client finishes writing the file, it calls close() on the stream.
7. This flushes all the remaining packets to the DataNode pipeline and waits for relevant acknowledgments before communicating with the NameNode to inform the client that the creation of the file is complete.


# Word count using map-reduce

```java
import java.io.IOException;
import java.util.StringTokenizer;
import org.apache.hadoop.io.*;
import org.apache.hadoop.mapreduce.*;
import org.apache.hadoop.conf.Configuration;
import org.apache.hadoop.fs.Path;
import org.apache.hadoop.mapreduce.lib.input.FileInputFormat;
import org.apache.hadoop.mapreduce.lib.output.FileOutputFormat;

public class WordCountRedu {

    public static class MapClass extends Mapper<Object, Text, Text, IntWritable> {
        private final static IntWritable one = new IntWritable(1);
        private Text word = new Text();
        public void map(Object k, Text v, Context c) throws IOException, InterruptedException {
            StringTokenizer st = new StringTokenizer(v.toString());
            while (st.hasMoreTokens()) {
                word.set(st.nextToken());
                c.write(word, one);
            }
        }
    }

    public static class ReduceClass extends Reducer<Text, IntWritable, Text, IntWritable> {
        public void reduce(Text k, Iterable<IntWritable> vals, Context c) throws IOException, InterruptedException {
            int sum = 0;
            for (IntWritable v : vals) sum += v.get();
            c.write(k, new IntWritable(sum));
        }
    }

    public static void main(String[] a) throws Exception {
        Job j = Job.getInstance(new Configuration(), "Word Count");
        j.setJarByClass(WordCountRedu.class);
        j.setMapperClass(MapClass.class);
        j.setReducerClass(ReduceClass.class);
        j.setOutputKeyClass(Text.class);
        j.setOutputValueClass(IntWritable.class);
        FileInputFormat.addInputPath(j, new Path(a[0]));
        FileOutputFormat.setOutputPath(j, new Path(a[1]));
        j.waitForCompletion(true);
    }
}

```

# Yarn architecture

![Pasted image 20251010213934.png](/img/user/Pasted%20image%2020251010213934.png)

1. A client program submits the application which includes the necessary specifications to launch the application-specific ApplicationMaster itself.
2. The ResourceManager launches the ApplicationMaster by assigning some container.
3. The ApplicationMaster, on boot-up, registers with the Resource Manager. This helps the client program to query the Resource Manager directly for the details.
4. During the normal course, ApplicationMaster negotiates appropriate resource containers via the resource-request protocol.
5. On successful container allocations, the ApplicationMaster launches the container by providing the container launch specification to the Node Manager.
6. The NodeManager executes the application code and provides necessary information such as progress, status, etc. to it’s ApplicationMaster via an application-specific protocol.
7. During the application execution, the client that submitted the job directly communicates with the ApplicationMaster to get status, progress updates, etc. via an application-specific protocol.
8. Once the application has been processed  completely, ApplicationMaster deregisters with the  Resource Manager and shuts down, allowing its own container to be repurposed.