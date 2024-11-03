# DevOps Assignment: Debugging and Running a Dockerized Application
***********
## Build Docker images and launch containers
In .yaml file, edit the file and add the path of the dockerFile for both nginx and python.
- docker-compose.yaml file :
![image](https://github.com/user-attachments/assets/464b26fd-e98b-47f2-9ef0-768130e60b17)

- In Docker Desktop ss :
![image](https://github.com/user-attachments/assets/2f60a235-21a4-4e90-8a6f-08b938dc9c1c)
***********

## Debug and resolve intentional errors in the code to ensure the application runs correctly.
Step 1: Correct the Python Dockerfile
- Typo in the WORKDIR path (/appp should be /app).
- Incorrect file name in COPY command (appy.py should be app.py).
- Incorrect RUN command for installing packages (netiface should be netifaces).
- Incorrect EXPOSE syntax (should not use quotes).
- Typo in the CMD command (pythn should be python).
- The port specified in the CMD is incorrect (should be 8000).

Step 2: Correct the Nginx Dockerfile
- Typo in the base image (latests should be latest).
- Incorrect file name in COPY command (nginix.conf should be nginx.conf).
- Incorrect destination path in COPY command (/usr/share/nginx/htmll should be /usr/share/nginx/html).
- Incorrect EXPOSE syntax (should not use quotes).
- Typo in the CMD command (daemon of; should be daemon off;).

Step 2: Correct the Nginx Configuration File
- Typo in worker_connection (should be worker_connections).
- Incorrect path in include directive (/etc/nginx/mime.typess should be /etc/nginx/mime.types).
- Incorrect directive name (default_typ should be default_type).
- Ensure that the proxy URL matches the service name in docker-compose.yaml.

Step 3: Correct the Docker Compose File
- image names should be consistent with what you build.
- Incorrect port mapping ("eighty:80" should be "80:80").
- Incorrect volume path (nginx.confi should be nginx.conf).
- Incorrect expose syntax (should be ports).
- Typo in the network driver (bridg should be bridge).
- Typo in the network options (compelex_option should be complex_option).
***********

## Verify the application in your browser.
![image](https://github.com/user-attachments/assets/5e907170-b629-4320-90b7-bd58f418e834)

![Screenshot (222)](https://github.com/user-attachments/assets/776cec7f-cb8b-45dd-9509-a763d6df5419)

- docker-compose logs nginx 
![image](https://github.com/user-attachments/assets/d09d9798-fbf2-43dd-9ff3-1f0f5313cd43)

- docker-compose logs python-app
![image](https://github.com/user-attachments/assets/57d939a6-5a60-4e16-abbe-07e3ccc691b2)


