# Install-Guides

`wget -qO- https://raw.githubusercontent.com/TheHive-Project/TheHive/master/PGP-PUBLIC-KEY | sudo gpg --dearmor -o /usr/share/keyrings/thehive-project-archive-keyring.gpg"`

##Make A New file called /etc/apt/sources.list.d/thehive-project.list and put this in there.

`# /etc/apt/sources.list.d/thehive-project.list
deb [signed-by=/usr/share/keyrings/thehive-project-archive-keyring.gpg] https://deb.thehive-project.org release main1`

#Signuature Not Working

`deb [trusted=yes] https://deb.thehive-project.org release main`

#Run this after 

`sudo apt update`

`sudo apt install cortex`

#Go to this file and generate a key for play.http.secret.key = "SOME_RANDOM_SECRET_KEY".

`sudo nano /etc/cortex/application.conf`

#Use this to generate a random key and also uncomment it.

`openssl rand -hex 32`

#Enable cortex

`sudo systemctl enable --now cortex`

#Check the status of cortex

`sudo systemctl status cortex`

#Start cortex

`sudo systemctl start --now cortex`

DOCKER INSTALL

#Install Packages

`#apt install wget gnupg apt-transport-https git ca-certificates ca-certificates-java curl  software-properties-common python3-pip lsb-release`

#Install Java

`sudo rpm --import https://yum.corretto.aws/corretto.key &> /dev/null
wget -qO- https://yum.corretto.aws/corretto.repo | sudo tee -a /etc/yum.repos.d/corretto.repo
yum install java-11-amazon-corretto-devel &> /dev/null
echo JAVA_HOME="/usr/lib/jvm/java-11-amazon-corretto" | sudo tee -a /etc/environment
export JAVA_HOME="/usr/lib/jvm/java-11-amazon-corretto"`

#Verify Java Version

`java -version`

#Install Key

`wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch |  sudo gpg --dearmor -o /usr/share/keyrings/elasticsearch-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/7.x/apt stable main" |  sudo tee /etc/apt/sources.list.d/elastic-7.x.list 
sudo apt install elasticsearch`

Install Key if it didn't work

`wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo gpg --dearmor -o /usr/share/keyrings/elasticsearch-keyring.gpg`

#Add the Elasticsearch APT Repo

`echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-7.x.list`

#Update the Machine

`sudo apt update`

#Add the missing GPG key

`wget -qO- https://raw.githubusercontent.com/TheHive-Project/TheHive/master/PGP-PUBLIC-KEY | gpg --dearmor | sudo tee /usr/share/keyrings/thehive-project-archive-keyring.gpg > /dev/null`

#Point the key in the right direction

`echo "deb [signed-by=/usr/share/keyrings/thehive-project-archive-keyring.gpg] https://deb.thehive-project.org release main" | sudo tee /etc/apt/sources.list.d/thehive-project.list`

#Update it

`sudo apt update`

#Edit this file

`sudo nano /etc/cortex/application.conf`

#Add a key

`openssl rand -hex 32`

#Start Cortex

`sudo systemctl enable --now cortex`

`sudo systemctl status cortex`

#Start Elasticsearch
`sudo systemctl enable elasticsearch`

`sudo systemctl start elasticsearch`

`sudo systemctl status elasticsearch`


#Optional command

`echo "deb [trusted=yes] https://deb.thehive-project.org release main" | sudo tee /etc/apt/sources.list.d/thehive-project.list
sudo apt update`

















