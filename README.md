Deployment Guide: EC2, Docker, Git, Maven Web App



1\.  Create Ubuntu Virtual Machine (AWS EC2)



Steps: - Login to AWS. - Go to Services → EC2 → Launch Instance. -

Configure: Name: ubuntu AMI: Ubuntu Server (Free tier) Architecture:

64-bit Instance type: t2.micro Key Pair: Create \& download .pem file

creatw AWS folder in desktop and copy (downloaded) file.HTML into AWS folder .

Security Group: Allow HTTP (80) \& HTTPS (443) Storage: 8GB - Launch the

instance.



Connecting to EC2: - Select instance → Connect. - Copy SSH command: ssh

-i “Key.pem” ubuntu@ - Open PowerShell/GitBash and run it.



2\.  Install Required Software in EC2



1.sudo apt update 2.sudo apt-get install docker.io  3.sudo apt install git

4\. sudo apt install nano 



5\. sudo docker ps  6. sudo docker version



3\.  Create Application \& Push to GitHub



\-   Create index.html in VS Code.



git init 

git add .

&nbsp;git commit -m “Initial commit” 

git branch -M main 

git remote add origin URL

git push -u origin main



OPEN POWERSHELL : 

&nbsp;	git clone <copied http url OF THAT INDEX.HTML REPO >

ls

cd reponame



Nano Dockerfile



Dockerfile content:

&nbsp;FROM nginx:alpine

&nbsp;COPY . /usr/share/nginx/html



Save file (Ctrl+O, Enter, Ctrl+X)



sudo docker build -t mywebapp .

sudo docker run -d -p 80:80 mywebapp



Open in browser: http://



open aws -> copy ipv4 address

paste it in browser

sudo docker ps

sudo docker contaId

open aws->instance->select the checkbox and instance state-> terminate->in launch AWS Academay learner lab lo click on AWS(end lab)-> yes



## ***MAVEN WEB PROJECT DEPLOYMENT IN AWS***

&nbsp;click on start lab

modules->aws academy learner lab->launch aws academy learner lab->start lab

click on EC2->click on launch instance->

give name as ManvenWebProjectExample->ubuntu->t2.micro->key pair->create new ket pair->name it :ExampleKey->.pem-> create keypair->Check all the boxes under network and click  on launch instance(ssh,https,http,)-> click on instance

wait unit 2 test passes->select the checkbox and click connect->copy ssh->

open terminal->cd AWS file->

run ssh cmd->sudo apt update

sudo apt-get install docker.io

y

sudo apt install git

sudo apt install nano

copy maven\_web url   -> clone clone url

ls

cd Maven\_web

nano Dockerfile

FROM tomcat:9-jdk11

COPY target/\*. war /usr/local/tomcat/webapps

ctrl-o,ctrl-x

sudo docker build -t mavenwebproject .

sudo docker run -d -p 9090:8080 mavenwebproject

select ckeck box and connect

copy public ipv4 

paste in browser

if not go to security click on security groups

click on edit inbound rules

add 9090
open -> cmd-> sudo docker run -d -p 9090:8080

sudo docker ps

sudo docker stop contId

sudo docker rm contId

open Aws-> instance-> select the checkbox of web-> instance states-> terminate->end lab



