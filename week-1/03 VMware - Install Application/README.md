# VMware - Install Application

* #### Lakukan SSH Server dari Terminal Macbook
![01](assets/01.png)

* #### Update Server menggunakan Command
    `sudo apt -y update && sudo apt -y upgrade`

![02](assets/02.png)

* #### Install Nginx Menggunakan Command dan Buka Dibrowser
    `sudo apt -y install nginx`

![03](assets/03.png)
![04](assets/04.png)

* #### Install Nodejs Versi 10 Menggunakan Command
    ```
    curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash
    sudo apt-get install -y nodejs
    ```

![05](assets/05.png)
![06](assets/06.png)

* #### Clone Repo Library dan Masuk Ke Direktori dengan menggunakan Command
    `git clone https://github.com/sgnd/library-frontend`

![07](assets/07.png)

* #### Lakukan Install npm package dan deploy dengan Command
    ```
    npm install
    npm start
    ```

![08](assets/08.png)
![09](assets/09.png)

* #### Buka Browser Masukkan Ip Adresses dengan port 3000

![10](assets/10.png)
