# Dockerized MongoDB with Node.js Express App

## Architecture

```
Host Machine
 └── Node.js Express App (localhost:5050)

Docker Containers
 ├── MongoDB Container (27017)
 └── mongo-express Container (8081)
```

## Technologies Used

**Use entity references for technologies people may explore:**

- Node.js
- Express.js
- MongoDB
- Docker
- Docker Compose

## Setup Instructions

- **First download nodejs app by below command.**

```
git clone git@github.com:aman-yadav-git/docker-guide.git
cd docker-nodejs-project
```

- Create file and add this 

```
vim mongodb.yaml
```

```
version: "3.8"

services:
  mongo:
    image: mongo
    ports:
      - "27017:27017"
    environment:
      MONGO_INITDB_ROOT_USERNAME: admin
      MONGO_INITDB_ROOT_PASSWORD: password

  mongo-express:
    image: mongo-express
    ports:
      - "8081:8081"
    environment:
      ME_CONFIG_MONGODB_ADMINUSERNAME: admin
      ME_CONFIG_MONGODB_ADMINPASSWORD: password
      ME_CONFIG_MONGODB_AUTH_DATABASE: admin
      ME_CONFIG_MONGODB_URL: mongodb://admin:root@mongo:27017/
```


- Start Node.js server

```
node server.js
```

- Start containers

```
docker compose -f mongodb.yaml up -d
```

- **Browse URLs**

```
Node API:
http://localhost:5050

Mongo Express:
http://localhost:8081
```

> we get API interface and database UI 

![image alt](https://github.com/aman-yadav-git/docker-guide/blob/main/docker-nodejs-project/image/app.png)
![image alt](https://github.com/aman-yadav-git/docker-guide/blob/main/docker-nodejs-project/image/datab.png)

- Let add data in database 
`http://localhost:8081`

>we will get this interface
![imagw alt](https://github.com/aman-yadav-git/docker-guide/blob/main/docker-nodejs-project/image/pasted%20file.png)

```
username: admin
password: pass
```
> its a standard login details 

- Now create database by name `xyzcollege-db`
![image alt](https://github.com/aman-yadav-git/docker-guide/blob/main/docker-nodejs-project/image/creatdb.png)

- Create User by name `users`
![image alt](https://github.com/aman-yadav-git/docker-guide/blob/main/docker-nodejs-project/image/creatuser.png)

- Click to New Document
![image alt](https://github.com/aman-yadav-git/docker-guide/blob/main/docker-nodejs-project/image/newdoc.png)

**Add below code and save it**

```
{
        "_id": ObjectId(),
    	"_id": ObjectId(),
		"username": "jane Doe",
		"email": "jane@gmail.com",
		"password": "password"

}
```

> Like this 
![image alt](https://github.com/aman-yadav-git/docker-guide/blob/main/docker-nodejs-project/image/code_user.png)

- And now browse this url  
`http://localhost:5050/getUser`

> you will view code that means database add successfully 
![image alt](https://github.com/aman-yadav-git/docker-guide/blob/main/docker-nodejs-project/image/getuser.png)

---
