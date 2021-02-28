# Repository

## Frontend
#### Git Clone https://github.com/sgnd/literature-frontend pada lokal
![01](asset/01.png)

#### ubah set-url githubnya dan tambahkan branch development dan production
![02](asset/02.png)

#### pada branch development tambah Dockerfile dan push 
```
FROM node:10
WORKDIR /usr/app
COPY . .
RUN npm install
EXPOSE 3000
CMD ["npm","start"] 
```
![03](asset/03.png)

#### Lakukan pada branch production juga tetapi isi Dockerfile diubah
```
FROM node:10
WORKDIR /usr/app
COPY . .
RUN npm install
RUN npm run build
RUN npm install -g serve
EXPOSE 5000
CMD ["serve","-s","build"] 
```
![04](asset/04.png)
![05](asset/05.png)



## Backend
#### git clone https://github.com/sgnd/literature-backend pada lokal sama seperti frontend tetapi teradapat perbedaan pada Dockerfile production dan development
```
FROM node:10
WORKDIR /usr/app
COPY . .
RUN npm install
EXPOSE 5000
CMD ["npm","start"] 
```
![06](asset/06.png)

#### pada production dockerfile
```
FROM node:10
WORKDIR /usr/app
COPY . .
RUN npm install
EXPOSE 5000
CMD ["npm","start","NODE_ENV=production"] 
```
![07](asset/07.png)
![08](asset/08.png)