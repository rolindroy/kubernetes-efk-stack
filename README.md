# kubernetes-efk-stack
Kubernetes EFK (Elasticsearch, FluentD, Kibana) Stack

## Introduction
When running multiple services and applications on a Kubernetes cluster, a centralized, cluster-level logging stack can help you quickly sort through and analyze the heavy volume of log data produced by your Pods. One popular centralized logging solution is the Elasticsearch, Fluentd, and Kibana (EFK) stack.

### Elasticsearch
Elasticsearch is a highly scalable open-source full-text search and analytics engine. It allows you to store, search, and analyze big volumes of data quickly and in near real time. It is generally used as the underlying engine/technology that powers applications that have complex search features and requirements.

For more, https://www.elastic.co/guide/en/elasticsearch/reference/current/getting-started.html

### Kibana
Kibana is an open source analytics and visualization platform designed to work with Elasticsearch. You use Kibana to search, view, and interact with data stored in Elasticsearch indices. You can easily perform advanced data analysis and visualize your data in a variety of charts, tables, and maps.

For more, https://www.elastic.co/guide/en/kibana/current/introduction.html
