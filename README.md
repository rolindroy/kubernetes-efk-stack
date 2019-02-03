# kubernetes-efk-stack
Kubernetes EFK (Elasticsearch, FluentD, Kibana) Stack

cluster.name: ProductionCluster
node.name: ELK01
network.host: [_eth0_, _local_]
http.port: 9200
discovery.zen.ping.unicast.hosts: ["100.96.2.3","100.96.1.4"]
bootstrap.system_call_filter: false
discovery.zen.minimum_master_nodes: 2
