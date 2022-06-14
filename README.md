### Basic FastAPI CRUD API

A Basic FastAPI based CRUD backend API without any database connection.

### How to use?

- Clone the Repo using: `git clone https://github.com/royaldevops/fastapi.git`
- Change Directory: `cd fastapi`
- Start Docker on your machine
- Use command: `sudo docker-compose up`

### How to Deploy on EC2 using NGINX and Docker?
- you can follow below steps or follow the article written by [Keshav Malik](https://dev.to/theinfosecguy/how-to-deploy-a-fastapi-application-using-docker-on-aws-4m61 ) 
1. Create an API using FastAPI by taking clone from How to use section.
2. Spin up your EC2 Instance
3. Install Docker and NGINX on your Server
```
$ sudo apt-get update
$ sudo apt-get install docker-ce docker-ce-cli containerd.io
$ sudo apt install nginx
```
4. Get all Application Files
```
$ git clone https://github.com/royaldevops/fastapi.git
```
5. Setup NGINX
- After installing NGINX and getting all our files, let's configure NGINX on our EC2 instance.
- Use the following command to create NGINX Config File
```
$ sudo vi /etc/nginx/sites-enabled/fastapi-demo
```
This will create a fastapi-demo file in the /etc/nginx/sites-enabled/ directory.

Paste the following server block in opened vi editor screen.

```
server {
    listen 80;
    server_name <PUBLIC_IP>;
    location / {
        proxy_pass http://127.0.0.1:8000;
    }
}
```

Replace <PUBLIC_IP> with the Public IP of your EC2 instance.

Save the file by pressing the Esc key and then typing :x and pressing Enter (Feel free to use any other text editor of your choice).

After saving the file, restart the NGINX server using the following command:

```
$ sudo service nginx restart
```

6. Start the Docker Container

    We will now start the Docker Container in Detached Mode so that Docker does not block our terminal. Use the following command to create the Docker container.
```
$ sudo docker-compose up -d
```
Here -d represents Detached Mode. This will start the Docker Container inside which our application is running.
