# Auth

#### Install apache2-utils dan buat password 
```
sudo apt-get install apache2-utils
sudo htpasswd -c ~/.htpasswd admin
```
![01](asset/01.png)
![02](asset/02.png)

#### edit file prometheus.conf dan tambahkan sesuai gambar
```
auth_basic "Prometheus";
auth_basic_user_file ~/.htpasswd;
```
![05](asset/05.png)

#### cek pada prometheus
![03](asset/03.png)

#### tambahkan auth basic di grafan
![04](asset/04.png)