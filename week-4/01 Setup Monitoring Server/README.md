# Setup Monitoring Server

* #### Security Group Monitoring Server
![01](assets/01.png)

* #### Install Docker pada Monitoring Server
![02](assets/02.png)

* #### Buat user prometheus dan direktori kebutuhan prometheus dengan command
```
sudo useradd -rs /bin/false prometheus
sudo mkdir /etc/prometheus
sudo mkdir -p /data/prometheus
```
![03](assets/03.png)

* #### Buat file `prometheus.yml`
```
cd /etc/prometheus/ && sudo touch prometheus.yml
```
![04](assets/04.png)

* #### Ubah permissions dengan command
```
sudo chown prometheus:prometheus /data/prometheus /etc/prometheus/*
```
![05](assets/05.png)

* #### Isi file `prometehus.yml`
```
global:
  scrape_interval: 5s
scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['10.0.1.207:9090']
  - job_name: 'node_exporter'
    scrape_interval: 10s
    target_groups:
      - targets: ['10.0.1.207:9100']
```
![06](assets/06.png)

* #### Jalankan Prometheus di docker dengan command
```
docker run -p 9090:9090 -d -v /etc/prometheus:/etc/prometheus prom/prometheus
```
![08](assets/08.png)

* #### Install Node-Exporter di docker dengan command
```
docker run -d --net="host" --pid="host" -v "/:/host:ro,rslave" quay.io/prometheus/node-exporter --path.rootfs=/host
```
![09](assets/09.png)

* #### Edit file `prometheus.yml` dan tambahkan node exporter
![10](assets/10.png)

* #### cek pada prometheus
![11](assets/11.png)

* #### Install Grafana di docker dengan command
```
docker run -d -p 3000:3000 --net=host grafana/grafana
```
![12](assets/12.png)

* #### Tambahkan Config pada Reverse Proxy dan lakukan configure SSL dengan command `sudo certbot --nginx -d monitoring.anjar.instructype.com` dan `sudo certbot --nginx -d prometheus.anjar.instructype.com`
```
 server {
        listen 80;
        listen [::]:80;

        server_name monitoring.anjar.instructype.com;

        location / {
                proxy_pass http://10.0.1.207:3000;
        }
}
```
![13](assets/13.png)
![14](assets/14.png)

![15](assets/15.png)
![16](assets/16.png)

* #### Masuk ke `monitoring.anjar.instructype.com` login ke grafana default login admin pass admin
![17](assets/17.png)