# DevOps Assignment: Debugging and Running a Dockerized Application


***********
---
## Build Docker images and launch containers
In .yaml file, edit the file and add the path of the dockerFile for both nginx and python.

- docker-compose.yaml file :
![image](https://github.com/user-attachments/assets/464b26fd-e98b-47f2-9ef0-768130e60b17)

- In Docker Desktop ss :
![image](https://github.com/user-attachments/assets/2f60a235-21a4-4e90-8a6f-08b938dc9c1c)
***********
---
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

- Access the application in your browser:
   Go to http://localhost to see the output from your Flask application.
![Screenshot (222)](https://github.com/user-attachments/assets/776cec7f-cb8b-45dd-9509-a763d6df5419)

- docker-compose logs nginx 
![image](https://github.com/user-attachments/assets/d09d9798-fbf2-43dd-9ff3-1f0f5313cd43)

- docker-compose logs python-app
![image](https://github.com/user-attachments/assets/57d939a6-5a60-4e16-abbe-07e3ccc691b2)

- On refreshing the web page timestamp is updated and it reflected in the log.
![image](https://github.com/user-attachments/assets/27ec6a5f-e30f-4f08-9bbb-de7641273102)
![image](https://github.com/user-attachments/assets/28cc2af3-62ff-439f-9a03-5ab7ec416b9d)

**** Hence Verified ****
***********

## Cloud Deployment
### Step-by-Step Guide to Deploy on AWS
1. Create an AWS Account
   - Login in at AWS.

2. Launch an EC2 Instance
   - Go to the EC2 Dashboard:
   - Navigate to the EC2 service in the AWS Management Console.

Launch Instance:
- Click on "Launch Instance."
- Choose an Amazon Machine Image (AMI) such that "Ubuntu Server".
- Choose an instance type.
- Click "Next" to configure instance details.
- Configure Security Group:
   - Create a new security group or select an existing one.
   - Add rules to allow HTTP (port 80) and, if necessary, HTTPS (port 443) traffic. Also, allow SSH (port 22) for remote access.
- Launch the Instance:
- Review your settings and click "Launch."
Select or create a key pair for SSH access, then click "Launch Instances."

3. Connect to Your EC2 Instance
Use SSH to connect to your instance. Open a terminal and run:
      ssh -i /path/to/your-key.pem ec2-user@<your-ec2-public-ip>

Replace /path/to/your-key.pem with the path to your key file and <your-ec2-public-ip> with your instance's public IP address.
in cmd :
![image](https://github.com/user-attachments/assets/43a3843e-72e3-4265-adab-ad9d4ebca0dc)

From this images, WE GET FOLLOWING CMD'S:
   1. Update the Package List:
   2. Upgrade Installed Packages:
   3. Install th docker on Ubuntu server
   4. Install Docker Compose
   5. Log Out and Back In
      - Exit the SSH session and reconnect to apply the user group changes
![image](https://github.com/user-attachments/assets/30302863-679e-4fd8-8385-3320d43d25cc)

   6. Use SCP to Copy Files: From your local machine, run:
         scp -i "C:\Users\aarsh\Downloads\devops_internship_challenge_key.pem" -r "C:\Users\aarsh\Downloads\devops-internship-challenge-main\devops-internship-challenge-main" ubuntu@ec2-3-110-176-9.ap-south-1.compute.amazonaws.com:/home/ubuntu/
   7.  cd /home/ubuntu/devops-internship-challenge-main
   8.  docker-compose build
   9.  docker-compose up -d
   10.  You can check the status of your running containers with:
![image](https://github.com/user-attachments/assets/46c96a46-b268-4575-86df-bca7277aa73f)
   11. AWS instance image, click on the Public IPv4 DNS link 
       ![image](https://github.com/user-attachments/assets/f6f94503-3788-46a0-b47f-e01d35a6e2b9)
   12. Output:
       ![image](https://github.com/user-attachments/assets/cdcbf631-27c5-44cd-bbf6-231668c72db3)
   13. Check the http for verification.
 *******************************************
 
