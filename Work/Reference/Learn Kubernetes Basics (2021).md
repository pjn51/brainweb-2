---
author: 
rating:
genre: STEM
format: article
---
# Learn Kubernetes Basics
`LINKS:` [source](https://kubernetes.io/docs/tutorials/kubernetes-basics/)
`TAGS:` #article #wip 
`AUTHOR:` N/A

---
# Introduction
## Kubernetes basics
The article starts off by outlining its purpose. This is a tutorial providing a walkthrough of the basics of the [[Kubernetes]] cluster orchestration system. We can learn how to deploy a containerized application on a cluster, scale that deployment, update the containerized application with a new software version, and debug the containerized application. 

Describing the setup for the tutorial, the article says that this uses Kataconda to run a virtual terminal in our web browser that runs Minikube, a small-scale local deployment of Kubernetes. Therefore, we don't have to install anything to work within this tutorial. 

## What can Kubernetes do for you?
The article outlines the advantages of Kubernetes. The "[[containierization]]" that Kubernetes provides allows applications to be updated and released without any downtime. 

# Using Minikube to create a cluster
## Kubernetes clusters
The article explains that Kubernetes coordinates a highly available cluster of computers that can work as a single unit. This means we can deploy applications without tying them to any single machine. But in order to do this, we have to package those applications so they can be decoupled from individual hosts - this is the reason for containeriziation. 

The article describes the benefits of containerization. These applications are more flexible, more available, and can get resources automatically allocated to them from multiple computers using Kubernetes. 

Turning to Kubernetes clusters, the article says that clusters consist of a *control pane* that coordinates the cluster, and the *nodes* that perform work and run applications. 

### Cluster diagram
<center>
	<img src='https://d33wubrfki0l68.cloudfront.net/283cc20bb49089cb2ca54d51b4ac27720c1a7902/34424/docs/tutorials/kubernetes-basics/public/images/module_01_cluster.svg'>
</center>

The article says that the control pane is responsible for managing the cluster. It coordinates activities like scheduling applications, maintaining desired states, scaling apps, and rolling out updates. A node is a virtual machine or a physical computer that serves as a worker machine in a Kubernetes cluster. Each node has a *Kubelet,* which is an agent for managing the node and communicting with the control pane. 

Turning to this node, the article says that each node must have tools for handling container operations like containerd or Docker. There should be at least three nodes for a cluster meant to handle production traffic. 

# Using kubectl to create a deployment
## Kubernetes deployments
...