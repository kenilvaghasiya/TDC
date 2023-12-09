
<p align="center">
  <img src="image.png" alt="Alt text"/>
</p>

<h1 align="center">CECS 574 Topics in Distributed Computing</h1>


## Course Details

- **Instructor**: Dr. Pooria Yaghini
- **Department**: Computer Engineering and Computer Science
- **Term**: Fall 2023
- **Institution**: California State University, Long Beach

## Team Members

1. **Dhruv Jigneshkumar patel** - ID: 030833684 - Email: [DhruvJigneshkumar.patel01@student.csulb.edu](mailto:DhruvJigneshkumar.patel01@student.csulb.edu)
2. **Kenil Vaghasiya** - ID: 030747611 - Email: [kenilprakashbhai.vaghasiya01@student.csulb.edu](mailto:kenilprakashbhai.vaghasiya01@student.csulb.edu)
3. **Priya Sunilkumar Shah** - ID: 030824675 - Email: [PriyaSunilkumar.Shah01@student.csulb.edu](mailto:PriyaSunilkumar.Shah01@student.csulb.edu)
4. **Meet Sunilkumar Shah** - ID: 030824662 - Email: [Meet.Shah01@student.csulb.edu](mailto:Meet.Shah01@student.csulb.edu)


# Hadoop Single Node Clustering

This repository provides comprehensive guidelines for setting up a single-node Hadoop cluster, primarily for educational and development purposes. Hadoop, a powerful distributed data processing framework, can be effectively learned and tested in this simplified environment.

# Our Motivation behind undertaking this project

The motivation behind undertaking a Hadoop single-node clustering project lies in harnessing the power of distributed computing to efficiently process and analyze large volumes of data. As organizations grapple with ever-expanding datasets, the need for scalable and cost-effective solutions becomes paramount. Hadoop, with its distributed file system and MapReduce programming model, offers a robust framework for parallel processing, enabling us to handle substantial data loads seamlessly. By implementing a single-node cluster, we aim to gain hands-on experience in deploying, configuring, and managing Hadoop on a smaller scale, laying the groundwork for future scalability. This project not only facilitates a deeper understanding of distributed computing principles but also equips us with practical skills essential for addressing real-world challenges in data-intensive environments.

# Problems and real time challenges that can be solved using HDFS

Hadoop Distributed File System (HDFS) is designed to address challenges associated with the storage and processing of massive datasets. Some key problems that Hadoop DFS can help solve include:

1. _Scalable Storage:_ HDFS allows for the storage of vast amounts of data across a distributed cluster of machines, enabling seamless scalability as data volumes grow.

2. _Fault Tolerance:_ Hadoop DFS ensures fault tolerance by replicating data across multiple nodes. In the event of node failure, the system can still access data from replicas on other nodes, maintaining data integrity and availability.

3. _Parallel Processing:_ Hadoop DFS, coupled with the MapReduce programming model, facilitates parallel processing of data. This accelerates data processing tasks by distributing the workload across multiple nodes in the cluster.

4. _Cost-Effective Storage:_ HDFS is designed to run on commodity hardware, providing a cost-effective solution for storing and managing large datasets without the need for expensive storage infrastructure.

5. _Data Locality:_ Hadoop optimizes data processing by bringing computation closer to the data. It ensures that tasks are scheduled on nodes where the data is already stored, minimizing data transfer across the network and improving overall performance.

6. _Data Replication:_ By replicating data across nodes, Hadoop DFS provides data redundancy, reducing the risk of data loss due to hardware failures. This feature enhances data durability and reliability.

7. _Support for Unstructured Data:_ Hadoop DFS accommodates diverse data types, including unstructured data like images, videos, and text. This flexibility makes it suitable for a wide range of applications and industries.

8. _Batch Processing:_ Hadoop DFS is well-suited for batch processing of large datasets, enabling the efficient execution of complex analytics and data transformation tasks.

By addressing these challenges, Hadoop DFS empowers organizations to efficiently manage, process, and derive insights from massive volumes of data, making it a valuable solution for various industries and use cases.

# Technologies

- Hadoop 3.3.6
- intellij IDE
- VScode
- Java programming language
- xml configurations

# learnings

Hadoop Distributed File System (HDFS) is designed to address challenges associated with the storage and processing of massive datasets. Some key problems that Hadoop DFS can help solve include:

1. _Scalable Storage:_

2. _Fault Tolerance:_

3. _Parallel Processing:_

4. _Cost-Effective Storage:_

5. _Data Locality:_

6. _Data Replication:_

7. _Support for Unstructured Data:_

8. _Batch Processing:_

# Prerequisites

Ensure these components are installed on your system before proceeding:

- Java Development Kit (JDK) 8
- Hadoop (version 3.3.6 recommended)
- [Optional] Additional Hadoop ecosystem components (e.g., Hive, Pig, HBase)

## Installation and Configuration

## Step 1: Download

- Begin by downloading the necessary code from the repository.

## Step 2: Configuration

- Navigate to hadoop-3.3.6/etc and perform the following edits:

## 2.1 yarn-site.xml

- Insert these settings within the tags:

        <configuration>
        <property>
        <name>yarn.nodemanager.aux-services</name>
        <value>mapreduce_shuffle</value>
        </property>
        <property>
        <name>yarn.nodemanager.aux-services.mapreduce.shuffle.class</name>
        <value>org.apache.hadoop.mapred.ShuffleHandler</value>
        </property>
        <property>
        <name>yarn.resourcemanager.hostname</name>
        <value>127.0.0.1</value>
        </property>
        <property>
        <name>yarn.acl.enable</name>
        <value>0</value>
        </property>
        <property>
        <name>yarn.nodemanager.env-whitelist</name>
        <value>JAVA_HOME,HADOOP_COMMON_HOME,HADOOP_HDFS_HOME,HADOOP_CONF_DIR,CLASSPATH_PERPEND_DISTCACHE,HADOOP_YARN_HOME,HADOOP_MAPRED_HOME</value>
        </property>
        <property>
        <name>yarn.nodemanager.local-dirs</name>
        <value>datanode/hadoop/yarn/local</value>
        </property>
        <property>
        <name>yarn.nodemanager.log-dirs</name>
        <value>datanode/hadoop/yarn/log</value>
        </property>
        </configuration>

## 2.2 core-site.xml

Add this configuration:

    <configuration>
    <property>
    	<name>fs.defaultFS</name>
    	<value>hdfs://localhost:9000</value>
    </property>
    </configuration>

## 2.3 hdfs-site.xml

Include the following:

    <configuration>
    <property>
    	<name>dfs.replication</name>
    	<value>1</value>
    </property>
    <property>
    	<name>dfs.namenode.name.dir</name>
    	<value>C:\hadoop-3.3.6\data\namenode</value>
    </property>
    <property>
    	<name>dfs.datanode.data.dir</name>
    	<value>C:\hadoop-3.3.6\data\datanode</value>
    </property>

    </configuration>

## 2.4 mapred-site.xml

Insert:

    <configuration>
    <property>
    	<name>mapreduce.framework.name</name>
    	<value>yarn</value>
    </property>
    </configuration>

# Step 3: Create Local Directories

Under hadoop-3.3.6/, create a data directory with subdirectories namenode and datanode.

# Step 4: Command Line Operations

Execute these commands:

## Format the namenode: hadoop namenode -format

## Start DFS: start-dfs.cmd

## Start YARN: start-yarn.cmd

## Verify daemon operations: jps

## Create a Hadoop FS directory: hadoop fs -mkdir /input

## Upload a file: hadoop fs -put <filename> /input

## Run MapReduce job: hadoop jar <jarfile> <MainClass> /input /output

Troubleshooting

# If you encounter abrupt stops with datanode, namenode, resourcemanager, or nodemanager, it's likely due to misconfiguration or incompatible JDK versions. The configurations provided here are verified, but if issues persist, please contact for further assistance.

For additional support, reach out at

dhruv.21patel01@gmail.com.

# Credits

Students of California State University

- Dhruv jigneshkumar patel
- Priya sunilkumar shah
- Meet sunilkumar shah
- Kenil vaghasiya

- Guided By professor Pooria Yaghini
