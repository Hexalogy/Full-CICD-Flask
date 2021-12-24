
# Full-CICD-Flask

1x EC2 Micro for Flask
1x EC2 Micro for Jenkins


## Install Flask
### Install Git
Check if Git is installed:
```
git --version
```
### Install Docker
```
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

## Install Jenkins
### Allow port 8080 on EC2
Create a security group to allow inbound of port 8080 on EC2

### Setup Jenkins
1. Create jenkins.sh
```
#!/bin/bash
sudo apt update

#Installing Java 8 which is pre-req
sudo apt install default-jre -y
sudo apt install default-jdk -y

#Install Jenkins
wget -qO - https://pkg.jenkins.io/debian-stable/jenkins.io.key | apt-key add -

sudo sh -c 'echo deb http://pkg.jenkins-ci.org/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'

sudo apt update
sudo apt install jenkins -y
sudo systemctl start jenkins
sudo systemctl status jenkins
```
2.  Execute following commands
```
#to make the script executable
sudo chmod +7 script-name.sh

#to execute the script
sudo ./script-name.sh
```
It will provide the output something like.

![image](https://user-images.githubusercontent.com/9726028/147325775-9cc6ac2f-11fa-433a-95d4-bb2c6150b50e.png)

3. Setup Jenkins

Go to Jenkins UI by entering your server’s IP address on port 8080 as Jenkins is hosted on port 8080 by default.

It will bring the Unlock Screen on first time as show below.

![image](https://user-images.githubusercontent.com/9726028/147325809-654d3088-3c09-4ac4-bae8-db20b28418b1.png)

As directed on the screen, get the admin password by executing the command
```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
Enter the password you received in Administrator password field and click on “Continue”.

Next click in the recommended option of “Install suggested plugins”

https://miro.medium.com/max/700/1*y0RL0OMGExb6NIJraoiy_A.png


