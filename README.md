# SOFTWAREENGINEERING
Deployment Guide: EC2, Docker, Git, Maven Web App

1.  Create Ubuntu Virtual Machine (AWS EC2)

Steps: - Login to AWS. - Go to Services → EC2 → Launch Instance. -
Configure: Name: ubuntu AMI: Ubuntu Server (Free tier) Architecture:
64-bit Instance type: t2.micro Key Pair: Create & download .pem file
creatw AWS folder in desktop and copy (downloaded) file.HTML into AWS folder .
Security Group: Allow HTTP (80) & HTTPS (443) Storage: 8GB - Launch the
instance.

Connecting to EC2: - Select instance → Connect. - Copy SSH command: ssh
-i “Key.pem” ubuntu@ - Open PowerShell/GitBash and run it.

2.  Install Required Software in EC2

1.sudo apt update 2.sudo apt-get install docker.io  3.sudo apt install git
4. sudo apt install nano 

5. sudo docker ps  6. sudo docker version

3.  Create Application & Push to GitHub

-   Create index.html in VS Code.

git init 
git add .
 git commit -m “Initial commit” 
git branch -M main 
git remote add origin URL
git push -u origin main

4.  Clone App & Create Dockerfile on EC2

git clone cd nano Dockerfile

Dockerfile content: FROM nginx:latest COPY . /usr/share/nginx/html

Save file (Ctrl+O, Enter, Ctrl+X)

5.  Build Docker Image

sudo docker build -t mywebapp .

6.  Run Docker Container

sudo docker run -d -p 80:80 mywebapp

Open in browser: http://

7.  Maven Web Project Deployment

Install Maven: sudo apt update sudo apt install maven -y

Clone Maven project: git clone cd

Build Docker image: sudo docker build -t mavenwebapp .

Run container: sudo docker run -d -p 9090:8080 mavenwebapp

If page not loading: - Add inbound rule in Security Group: port 9090,
0.0.0.0/0

Access app: http://:9090

Terminate EC2 after testing.
