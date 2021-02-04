# Deployment Backend

* #### git clone ke repo dikrektori library backend dengan command
`git clone git@github.com:anjardanis/library-backend.git`
![01](assets/01.png)

* #### Ubah Branch Menjadi ke Branch Deploy
![11](assets/11.png)

* #### install nodejs versi 10
```
curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash
sudo apt-get install -y nodejs
```
![02](assets/02.png)

* #### install packages `npm install` dan `npm install nodemon` dan pm2 `sudo npm install -g pm2` dan buat file `ecosystem.config.js`
![03](assets/03.png)
![04](assets/04.png)

```

module.exports = {
        apps: [
          {
            name: 'library',
            script: 'npm',
            args: 'start'
           }
        ]
};
```

* #### install packages untuk migrate database dengan command `sudo npm install -g sequelize-cli` 
![05](assets/05.png)

* #### ubah isi file `/config/config.json` dan isi sesuai ip database
![06](assets/06.png)

* #### Masuk ke mysql server database dengan command `mysql -u 'username' -h 'ip-server-db' -p` dan buat database dengan command `create database library;`
![07](assets/07.png)

* #### lakukan migrasi database dengan command `sequelize db:migrate all` jika gagal install `sudo npm install -g mysql2` terlebih dahulu
![08](assets/08.png)

* #### jalankan command `pm2 start ecosystem.config.js`
![09](assets/09.png)

## Pada Frontend Server

* #### edit file di server frontend pada /config/config.js dan ganti base url dengan ip backendserver dan lakukan command `pm2 restart 0`
![10](assets/10.png)
