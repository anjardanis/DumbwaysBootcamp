# User

#### Install Ansible dengan script
![01](asset/01.png)

#### Jalankan dengan chmod +x dan ./
![02](asset/02.png)

#### git clone repo ansible
![05](asset/05.png)
![03](asset/03.png)
![04](asset/04.png)

#### cek ssh target server menggunakan ssh key
![06](asset/06.png)

#### cek ping ke semua server target
![07](asset/07.png)

#### lakukan apt update dan apt upgrade dengan command
```
ansible all -m apt -a update_cache=true --become
ansible all -m apt -a "upgrade=dist" --become
```
![08](asset/08.png)
![09](asset/09.png)

#### install docker dan docker compose plus install node exporter
![10](asset/10.png)
![11](asset/11.png)

#### Buat User baru dan ssh-keygen
![12](asset/12.png)
![13](asset/13.png)