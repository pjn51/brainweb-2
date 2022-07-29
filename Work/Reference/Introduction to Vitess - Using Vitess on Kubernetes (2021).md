---
author: Roman Doroschevici
rating:
genre: STEM
format: article
---
# Introduction to Vitess - Using Vitess on Kubernetes
`LINKS:` [source](https://rancher.com/blog/2018/2018-08-31-intro-to-vitess-on-kubernetes/)
#article #wip 
`AUTHOR:` Roman Doroschevici

---
# A Vitess overview
The article begins by describing what [[Vitess]] is. It's a [[database]] cluster solution for deploying, managing, and scaling large clusters of[[ MySQL]] instances. 

The author describes a basic scenario. We would have a master instance, and a couple replicas of that instance. We would then direct read-only queries to the replicas and write queries to the master instance. 

<center>
	<img src='https://rancher.com/img/blog/2018/mysql_default_setup.png'>
</center>

This works fine, Roman continues, until we run into hardware limitations. Query monitoring becomes increasingly difficult if we manually "shard" the database. This was the reason that researchers came up with Vitess. 

The author examines the benefits of Vitess. In terms of performance, we can optimize performance by having "multiplex" front-end application queries onto a "pool" of MySQL connections. We can de-dupe queries by reusing results of "in-flight" queries for identical requests recieved during execution. WE can also limit the number of concurrent transactions to optimize throughput.

In terms of protection, the article explains, Vitess allows for query "sanitation" to avoid "non-deterministic updates." It can also terminate queries that take too long, and specify "access control lists (ACLs)" for each table, based on the connected user.

For monitoring, Roman says, Vitess has tools for monitoring performance and diagnosing problems. We can also see a list of incoming queries, and a list of changing rows in the database. 

Roman outlines the rest of this article. We will deploy a Rancher 2.0 instance, and use it to create a Kubernetes cluster. We will then deploy Vitress on the Kubernetes cluster, create a database on Vitress, and query it. Then, we will deploy a test application in the Kubernetes cluster that will use Vitress. 

# Deploy a Rancher 2.0 instance and start a Kubernetes cluster
I'm going to pause here because I don't yet know what [[Rancher]] is, or what [[Kubernetes]] means. 