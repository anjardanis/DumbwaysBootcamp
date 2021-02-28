# Jenkins

#### Run Jenkins Docker dari Server Ansible
![01](asset/01.png)

#### Cat password jenkins dengan command 
```
ansible cicd -m shell -a 'docker exec cicd cat /var/jenkins_home/secrets/initialAdminPassword' -bK
```
![02](asset/02.png)

#### Masukkan Password Jenkins
![03](asset/03.png)

#### Install Plugin Publish Over SSH dan Discord Notifier
![04](asset/04.png)

#### Buat Token untuk menghubungan jenkins dan github
![05](asset/05.png)
![06](asset/06.png)

#### Buat Credential username github
![07](asset/07.png) 

#### tambahkan webhook gituhub di konfigurasi jenkins
![08](asset/08.png)

#### SSH-copy-id dari server jenkins ke frontend dan backend server
![09](asset/09.png)

#### tambahkan konfigurasi jenkins di publish over ssh menggunakan id_rsa private
![10](asset/10.png) 
![11](asset/11.png)

#### Buat Jenkins Job untuk frontend dan backend
![12](asset/12.png)
![13](asset/13.png)
![14](asset/14.png)

```
cd /home/frontend01/literature-frontend
git pull origin production
docker-compose down
docker rmi anjardanis/literature-frontend
docker build -t anjardanis/literature-frontend .
docker-compose up -d
```
![15](asset/15.png)
![16](asset/16.png)
![17](asset/17.png)
![18](asset/18.png)

```
cd /home/backend01/literature-backend
git pull origin production
docker-compose down
docker rmi anjardanis/literature-backend
docker build -t anjardanis/literature-backend .
docker-compose up -d
```
![19](asset/19.png)
![20](asset/20.png)