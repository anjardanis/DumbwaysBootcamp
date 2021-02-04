# SSL Configuration for Backend Application

* #### Dikarenakan sudah install lets'encyyrpt packages pada minggu 1 selanjutnya hanya command
```
sudo add-apt-repository ppa:certbot/certbot
sudo apt-get update
sudo apt-get install -y python-certbot-nginx
```
`sudo certbot --nginx -d api.anjar.instructype.com` pilih 2.

![01](assets/01.png)

* #### ganti file config.js pada frontend bagian base url diganti `https://api.anjar.instructype.com/` dan restart pm2
![03](assets/03.png)

* #### Hasil Output:
![02](assets/02.png)