# AWS - Server for Application

* #### 1. Persiapan Frontend Applikasi Library di Private Server
Pertama Ubah Nama Private Server menjadi Application-Frontend-1
![01](assets/01.png)

Duplicate Application-Frontend-1 dengan cara Pilih Servernya Klik Action > Images & Templates > Launch More Like This
![02](assets/02.png)

Kemudian Klik Launch dan Ubah Namanya Menjadi Application-Frontend-2
![03](assets/03.png)
![04](assets/04.png)

* #### 2. Deploy Applikasi Library di Application-Frontend-1 dan Application-Frontend-2
* ##### Application-Frontend-1
SSH ke Server Application-Frontend-1 Melalui Public Server
![05](assets/05.png)

Update dan Upgrade OS dengan Command
`sudo apt update && sudo apt -y upgrade`
![06](assets/06.png)

Kemudian Install Nodejs Versi 10 dengan Command
```
curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash
sudo apt-get install -y nodejs
```
![07](assets/07.png)
![08](assets/08.png)

Clone Repo Library dan Masuk Ke Direktori dengan menggunakan Command
    `git clone https://github.com/sgnd/library-frontend`
![09](assets/09.png)

Buat file baru bernama `ecosystem.config.js` dan isi dengan pengaturan PM2
![10](assets/10.png)

Kemudian Install npm pm2 dengan command
    `sudo npm install -g pm2`
![11](assets/11.png)

Kemudian Jalankan pm2 dengan command
    `pm2 start ecosystem.config.js`
![12](assets/12.png)

* ##### Application-Frontend-2
Hampir sama dengan Application-Frontend-1 tetapi membuat username seperti pada Task 04 terlebih dahulu

Hasil Akhir Application-Frontend-2
![13](assets/13.png)