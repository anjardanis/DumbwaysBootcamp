# Install Git and SSH Key

* #### Fork Git Repository yang sudah diberikan 
![01](assets/01.png)

* #### SSH Ke server backend
![02](assets/02.png)

* #### Membuat ssh key dengan command `ssh-keygen`
![03](assets/03.png)

* #### copy key ke github
`cat ~/.ssh/id_rsa.pub`
![04](assets/04.png)

Masuk ke Github -> Setting -> SSH and GPG Keys -> Klik New SSH Key lalu copy dan klik add SSH key
![05](assets/05.png)
![06](assets/06.png)

* #### SSH ke Github dengan command `ssh -T git@github.com`
![07](assets/07.png)