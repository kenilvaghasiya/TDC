# Hadoop Single Node Clustering

This repository provides comprehensive guidelines for setting up a single-node Hadoop cluster, primarily for educational and development purposes. Hadoop, a powerful distributed data processing framework, can be effectively learned and tested in this simplified environment.

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
- Insert these settings within the <configuration> tags:

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