# Connect Multiple Server

* #### Install Node-Exporter pada semua target server (frontend,backend,database,nginx,cicd) dan buka port 9100
```
docker run -d --net="host" --pid="host" -v "/:/host:ro,rslave" quay.io/prometheus/node-exporter --path.rootfs=/host
```
![01](assets/01.png)
![02](assets/02.png)
![03](assets/03.png)

* #### edit file `prometheus.yml` dan tambahkan ip target
![08](assets/08.png)

* #### Cek pada prometheus.anjar.instructype.com
![09](assets/09.png)

* #### tambahkan prometheus pada grafana
![10](assets/10.png)

* #### Setting dashboard frontend backend
![11](assets/11.png)
![12](assets/12.png)

Untuk Query
CPU Usage
```
100 - (avg by(instance)(irate(node_cpu_seconds_total{instance="10.0.1.249:9100",job="node_exporter",mode="idle"}[5m]))*100)
```
Memory Usage
```
(node_memory_MemTotal_bytes{instance="10.0.1.249:9100",job="node_exporter"} - (node_memory_MemFree_bytes{instance="10.0.1.249:9100",job="node_exporter"} +        
node_memory_Cached_bytes{instance="10.0.1.249:9100",job="node_exporter"} + node_memory_Buffers_bytes{instance="10.0.1.249:9100",job="node_exporter"} )) /   
node_memory_MemTotal_bytes{instance="10.0.1.249:9100",job="node_exporter"} * 100
```
Storage
```
node_filesystem_size_bytes{device="/dev/xvda1", fstype="ext4", instance="10.0.1.249:9100", job="node_exporter", mountpoint="/"}
```
```
node_filesystem_free_bytes{device="/dev/xvda1", fstype="ext4", instance="10.0.1.249:9100", job="node_exporter", mountpoint="/"}
```

Network
```
node_network_transmit_bytes_total{device="eth0", instance="10.0.1.249:9100", job="node_exporter"}
```
```
node_network_receive_bytes_total{device="eth0", instance="10.0.1.249:9100", job="node_exporter"}
```