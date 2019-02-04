# kubernetes-efk-stack
Kubernetes EFK (Elasticsearch, FluentD, Kibana) Stack

## Introduction
When running multiple services and applications on a Kubernetes cluster, a centralized, cluster-level logging stack can help you quickly sort through and analyze the heavy volume of log data produced by your Pods. One popular centralized logging solution is the Elasticsearch, Fluentd, and Kibana (EFK) stack.

### Elasticsearch
Elasticsearch is a highly scalable open-source full-text search and analytics engine. 
[Read more](https://www.elastic.co/guide/en/elasticsearch/reference/current/getting-started.html)

### Kibana
Kibana is an open source analytics and visualization platform designed to work with Elasticsearch. 
[Read more](https://www.elastic.co/guide/en/kibana/current/introduction.html)

### FluentD
Fluentd is an open source data collector, which lets you unify the data collection and consumption for a better use and understanding of data. [Read more](https://docs.fluentd.org/v1.0/articles/quickstart)

### Instructions
Run the below commands in same order.

```
## Create namespace `kube-logging`
kubectl apply -f 000-namespace.yml

## Create elasticsearch discovery service (Port 9300)
kubectl apply -f 001-es-discovery-svc.yml

## Createt elasticsearch http port service (Port 9200)
kubectl apply -f 002-es-http-srv.yml

## Create kibana service with external loadbalancer
kubectl apply -f 003-kibana-srv.yml

## Create Elasticseach Cluster - StatefulSet
kubectl apply -f 004-es-cluster-stateful-app.yml

## Note: Wait till all the pods of the Elasticsearch cluster are up and running.
## Deploy Kibana Application
kubectl apply -f 005-kibana-app.yml

## Create service account for fluentd
kubectl apply -f 006-fluentd-service-account.yml

## Create RBAC Role based auth for fluentd to access pods and namespaces
kubectl apply -f 007-fluentd-rbac-auth.yml

## Attach the RABC Authentication with fluentD service account
kubectl apply -f 008-fluentd-cluster-binding.yml

## Create fluentD daemonset to run it on all the nodes
kubectl apply -f 009-fluentd-daemonet.yml

## Note: Kibana dashboard can be accessed by proxying Cluster IP of the kibana service or by using the load balancer url created by your cloud service provider.

```

### Reference

`Elasticsearch`  - [Docker Hub](https://hub.docker.com/r/rolindroy/elasticsearch), [Dockerfile](https://github.com/rolindroy/k8s-elasticsearch-php/blob/master/elasticsearch-db/6.6.0/Dockerfile)

`Kibana` - [Docker](https://www.elastic.co/guide/en/kibana/current/docker.html)

`FluentD` - [Docker Hub](https://hub.docker.com/r/fluent/fluentd/)

`Deployment` - [DigitalOcean Link](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-elasticsearch-fluentd-and-kibana-efk-logging-stack-on-kubernetes#step-4-%E2%80%94-creating-the-fluentd-daemonset)

