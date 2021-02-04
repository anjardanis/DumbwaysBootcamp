* # AWS Setup Database

* ## Konfigurasi Database Server
* #### SSH ke Database Server
![02](assets/01.png)

* #### install mysql di database server menggunakan command dan pilih versi 5.7
`wget https://dev.mysql.com/get/mysql-apt-config_0.8.15-1_all.deb`
![02](assets/02.png)

`sudo dpkg -i mysql-apt-config_0.8.15-1_all.deb`
![03](assets/03.png)
![04](assets/04.png)

`sudo apt update && sudo apt -y upgrade`
![05](assets/05.png)

`sudo apt -y install mysql-server` dan isikan password
![06](assets/06.png)
![07](assets/07.png)

* #### Buat user baru dan inisialisasi dengan backend server

```
mysql -u root -p

CREATE USER 'backend'@'10.0.1.123' IDENTIFIED BY 'anjar'; 

GRANT ALL PRIVILEGES ON *.* TO 'backend'@'10.0.1.123';

FLUSH PRIVILEGES;
```
catatan `'user'@'ip-backend' Identified By 'password';`

![08](assets/08.png)
![09](assets/09.png)

* #### bind ip adress backend dengan database dan ubah ip bind adress menjadi ip Database Server
`sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf` 
![10](assets/10.png)

* #### restart mysql
![11](assets/11.png)

* ## Konfigurasi Backend Server
* #### SSH ke server backend dan install mysql-client dengan command
```
sudo apt-get update

sudo apt-get install -y mysql-client
```
![12](assets/12.png)

* #### akses database server dari backend server menggunakan command
`mysql -u backend -h 10.0.1.58 -p`
![13](assets/13.png)