# AWS - Create and Setup Server

## Pertama Buat Virtual Private Cloud (VPC)

* #### 1. Membuat Elastic IP untuk Nat-Gateway
Klik Allocate Elastic IP Addres
![01](assets/01.png)

Kemudian Isi Tag Sesuai Gambar dan Klik Allocate
![02](assets/02.png)
![03](assets/03.png)

* #### 2. Buat VPC baru 
Klik Launch VPC Wizard
![04](assets/04.png)

Pilih VPC with Public and Private Subnet dan klik Select
![05](assets/05.png)

Isi Sesuai Pada Gambar Nama: DumbVPC ; IPv4 CIDR: 10.0.0.0/16 ; Public Subnet: 10.0.0.0/24 ; Private Subnet: 10.0.1.0/24
Elastic IP yg sudah dibuat akan digunakan di Elastic IP Allocation ID
![06](assets/06.png)

Kemudian Klik Create VPC
![07](assets/07.png)
![08](assets/08.png)

Untuk bagian Route Table, NAT Gateway sudah dibuat dapat dicek ditab Route Table dan berikan Nama Untuk Route Tables
Yang tersambung dengan Internet Gateway adalah Public Route Table dan yang tersambung dengan NAT adalah Private Route table
![09](assets/09.png)
![10](assets/10.png)

Kemudian Untuk Private Route Table attach dengan Private Subnet. dengan cara Pilih Private Route Table klik edit subnet associations
![11](assets/11.png)

Pilih Private Subnet dan klik Save

## Kedua Membuat Public Ubuntu Server dan Private Ubuntu Server

* #### 1. Membuat EC2 Instance untuk Public Server
Klik Launch Instances
![13](assets/13.png)

Pilih Ubuntu Server 18.04 LTS (HVM), SSD Volume Type Lalu Klik Select
![14](assets/14.png)

Kemudian Pilih Next:Configuration Instance Detail
![15](assets/15.png)

Untuk Bagian Network diganti dengan VPC: dumbVPC ; Subnet : Public Subnet Karena Public Server ; Autoassign: Enable Lalu Klik add storage
![16](assets/16.png)

Untuk Storage dibiarkan default yaitu 8 Gb Kemudian Klik add tags
![17](assets/17.png)

Untuk Tags Tambahkan Tag Sesuai gambar untuk memudahkan Lalu Klik Next:Configure Security Group
![18](assets/18.png)

Untuk bagian Security Group Isi Seperti pada Gambar. Lalu Klik Review and Launch dan Klik Launch
Port 22: Untuk SSH Ke Server
Port 80: Untuk HTTP
Port 443: Untuk HTTPS
![19](assets/19.png)

Keypair digunakan untuk SSH ke Server jika Belum membuat dibuat terlebih dahulu. Jika sudah klik launch Instances
![20](assets/20.png)
![21](assets/21.png)

Kemudian Gunakan Elastic IP untuk Public Server
![22](assets/22.png)

Kemudian Pilih Elasic yg baru dibuat dan klik Assosicate Elastic IP Address
![23](assets/23.png)

Pilih Instance Public Server yg baru dibuat dan Klik Associate
![24](assets/24.png)

Hasil Terakhir:
![25](assets/25.png)

* #### 2. Membuat EC2 Instance untuk Private Server

Klik Launch Instances
![13](assets/13.png)

Pilih Ubuntu Server 18.04 LTS (HVM), SSD Volume Type Lalu Klik Select
![14](assets/14.png)

Kemudian Pilih Next:Configuration Instance Detail
![15](assets/15.png)

Untuk Bagian Network diganti dengan VPC: dumbVPC ; Subnet : Private Subnet Karena Private Server ; Autoassign: disable Lalu Klik add storage
![26](assets/26.png)

Untuk Storage dibiarkan default yaitu 8 Gb Kemudian Klik add tags
![17](assets/17.png)

Untuk Tags Tambahkan Tag Sesuai gambar untuk memudahkan Lalu Klik Next:Configure Security Group
![27](assets/27.png)

Untuk bagian Security Group Isi Seperti pada Gambar. Lalu Klik Review and Launch dan Klik Launch
Port 22: Untuk SSH Ke Server dikarenakan untuk Keamanan Maka Port 22 Sourcenya adalah Security Group Public Server
Port 80: Untuk HTTP
Port 443: Untuk HTTPS
Port 3000: Untuk Deploy Frontend
![28](assets/28.png)

Keypair digunakan untuk SSH ke Server jika Belum membuat dibuat terlebih dahulu. Jika sudah klik launch Instances
![20](assets/20.png)
![21](assets/21.png)

Hasil Terakhir:
[29](assets/29.png)

* #### 3. SSH ke Public Server Menggunakan Terminal Macbook Air
Pilih Public Server Kemudian Klik Connect
![30](assets/30.png)

Pilih SSH Client
![31](assets/31.png)

Buka Terminal dan Pindah ke Direktori Terdapat keypair
![32](assets/32.png)

Copy Nomor 3 Yaitu `chmod 400 amazonkey.pem` dan bagian example `ssh -i "amazonkey.pem" ubuntu@ec2-34-233-242-103.compute-1.amazonaws.com`
![33](assets/33.png)

Hasil Terakhir dpt SSH ke Server Public
![34](assets/34.png)

* #### 4. Membuat New User di Public Server dan SSH Menggunakan password
Membuat User baru dengan Command
`sudo adduser anjardanispublic`
![35](assets/35.png)

Kemudian usermod User anjardanispublic dengan Command bertujuan untuk user tidak perlu menggunakan command dengan sudo didepannya
`sudo usermod -aG sudo anjardanispublic`
![36](assets/36.png)

Kemudian edit file `/etc/ssh/sshd_config` dan ubah PasswordAuthentication menjadi Yes
![37](assets/37.png)

Kemudian Restart dan Exit sshd Menggunakan Command
`sudo systemctl restart sshd`
![38](assets/38.png)

Kemudian SSH kembali dengan command `ssh user@ip` yaitu:
`ssh anjardanispublic@34.233.242.103`
![39](assets/39.png)

* #### 5. SSH Private Server dari Public Server
Dikarenakan Default Server AWS menggunakan keypair maka copy keypair ke dalam Public Server dengan cara membuat file keypair
![40](assets/40.png)
![41](assets/41.png)

Kemudian Sama dengan Langkah public Server Pilih Private Server dan Klik Connect dan kebagian SSH Client
![42](assets/42.png)

Copy Langkah nomor 3 dan example
![43](assets/43.png)

Hasil Akhir:
![44](assets/44.png)

* #### 6. Membuat New User di Private Server dan SSH Menggunakan password
Membuat User baru dengan Command
`sudo adduser anjardanisprivate`
![45](assets/45.png)

Kemudian usermod User anjardanispublic dengan Command bertujuan untuk user tidak perlu menggunakan command dengan sudo didepannya
`sudo usermod -aG sudo anjardanisprivate`
![45.5](assets/45.5.png)

Kemudian edit file `/etc/ssh/sshd_config` dan ubah PasswordAuthentication menjadi Yes
![46](assets/46.png)

Kemudian Restart dan Exit sshd Menggunakan Command
`sudo systemctl restart sshd`
![47](assets/47.png)

Kemudian SSH kembali dengan command `ssh user@ip` yaitu:
`ssh anjardanisprivate@10.0.1.109`
![48](assets/48.png)