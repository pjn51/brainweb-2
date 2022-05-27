# Hadoop
`TAGS:`

---
# Introduction [^1]
Apache Hadoop was released in 2005 as a [[distributed file system]] for storing large amounts of data. It is composed of the following modules:

1. Hadoop Common: supporting libraries and utilities for other modules.
2. Hadoop Distributed File System (HDFS): a [[distributed file system]] that stores data on the commodity machines. 
3. Hadoop YARN: a resource-management platform responsible for managing computational resources.
4. Hadoop MapReduce: a programming model for large scale data processing.

All of these modules are built to be resilient in the face of hardware failures, either of individual machines or multiple machines simultaneously. 

Any [[programming language]] can be used for the MapReduce module, although [[Java]] is common. There is also a [[SQL]] plugin called Apache Hive.

## HDFS
<center>
	<img src='https://opensource.com/sites/default/files/resize/images/life-uploads/hadoop-HighLevel_hadoop_architecture-640x460.png'>
</center>

HDFS is written in Java. Each *node* in a Hadoop instance has a single namenode and a cluster of datanodes form the HDFS cluster. 

This system can store large amounts of data (think gigabytes to terabytes) across multiple machines. It uses replication methods to make sure that no data can be lost. The typical replication value is three, meaning that each section of data is stored in three different locations across the system. Namenodes also have copies, called secondary namenodes. Their purpose is to hold snapshots of the namenode's directory information. 

## MapReduce
Above the file system sits the MapReduce engine. This contains a *JobTracker,* to which client applications can submit MapReduce jobs. The JobTracker pushes work to available *TaskTracker* nodes in the cluster. 

[^1]: https://opensource.com/life/14/8/intro-apache-hadoop-big-data