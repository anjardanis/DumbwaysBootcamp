# AWS - Reverse Proxy

## 1. Install Webserver nginx di Reverse Proxy Server
Ubah Nama Public Server Menjadi Reverse Proxy
![01](assets/01.png)

Update dan Upgrade OS di Reverse Proxy dengan Command
`sudo apt update && sudo apt -y upgrade`
![02](assets/02.png)

Kemudian Install Nginx dengan Command dan tes pada browser dengan menggunakan Public IPv4 address
`sudo apt -y install nginx`
![03](assets/03.png)
![04](assets/04.png)

Kemudian Pindah Ke Direktori `/etc/nginx/` kemudian buat direktori baru `dumblibrary` dan buat file `frontend.conf`
![05](assets/05.png)

isi file `frontend.conf`
```
    upstream frontend {
        server 10.0.1.109:3000;
        server 10.0.1.75:3000;
    }

    server {
	listen 80;
	listen [::]:80;

	server_name 34.233.242.103;

	location / {
		proxy_pass http://frontend;
	}
}
```
![06](assets/06.png)

Kemudian tambahkan folder dumblibrary di `nginx.conf`
![07](assets/07.png)

Restart Nginx dengan command
`sudo systemctl restart nginx`
![08](assets/08.png)

Hasil Akhir:
![09](assets/09.png)
