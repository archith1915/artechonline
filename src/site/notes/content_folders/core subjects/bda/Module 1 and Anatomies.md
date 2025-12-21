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