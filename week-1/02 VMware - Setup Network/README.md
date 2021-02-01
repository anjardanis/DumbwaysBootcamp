# VMware - Setup Network

* #### Ubah IP Menjadi Static Menggunakan Command
    `sudo nano /etc/netplan/00-installer-config.yaml`

* #### Isi File yaml seperti pada gambar dengan address 192.168.0.108/24 dengan DNS google [8.8.8.8, 8.8.4.4] 
![01](assets/01.png)

* #### kemudian Command `sudo netplan apply`
![1.5](assets/1.5.png)

* ### Cek IP menggunakan Command `ifconfig` dan Melalukan Ping Ke Google.com
![02](assets/02.png)