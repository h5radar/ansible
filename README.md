# Ansible
Ansible installer for h5radar application. Demo available at https://app.h5radar.com.

# How to install application
There are a few way to install application. The main difference related to SSL 
certification: self signed, let's encrypt or external files.

# Self signed certificates
* copy inventory/development/ files to inventory/production
* edit inventory/production/hosts to setup IPs
* run command ansible-playbook -v --diff --inventory inventory/production main.yml

# Lets encrypt certificates
* TODO: about public IP and DNS configuration
* copy inventory/development/ files to inventory/production
* edit inventory/production/hosts to setup IPs
* run command ansible-playbook -v --diff --inventory inventory/production main.yml

# Release application
* add release notes file to antora docs
* update version at antora.yml file
* run command: export COPYFILE_DISABLE=1 for MacOS
* run command: mvn release:prepare for java services
* run command: mvn release:perform for java services
* archive account service by command: tar -zcvf Binaries.tar.gz account*.jar
* archive radar service by command: tar -zcvf Binaries.tar.gz radar*.jar
* archive app-ui by command: tar -zcvf Binaries.tar.gz *
* setup version at antora.yml file at latest value
* create and publish the new releases at GitHub

# Setup environment
## MacOS environment
* run vagrant by command: vagrant up

## Linux environment
* export variables by command: export DEBIAN_FRONTEND=noninteractive 
* export variables by command: export NEEDRESTART_MODE=l
* export variables by command: export ANSIBLE_CONFIG=ansible.cfg
* update apt by command: sudo apt-get update
* install virtual env by command: sudo apt-get -y install python3-venv
* setup python env by command: python3 -m venv --upgrade-deps .venv && source .venv/bin/activate
* install pip packages by command: pip install --requirement requirements.txt
* install ansible requirements by command: ansible-galaxy install -r requirements.yml
* run vagrant by command: vagrant up

# Requirements
## OS
* [ ] Should support ubuntu 24

## SSL
* [ ] Should work with self signed certificates
* [ ] Should work with letsencrypted certificats (verify by http)
* [ ] Should work with letsencrypted certificats (verify by dns)

## Webserver
* [ ] Should work without proxy webserver  
* [ ] Should support apache2 with proxy 
* [ ] Should support nxinx with proxy* 

## Keycloak
* [ ] Should work without pre-installed keycloak  
* [ ] Should work with self installed keycloak 

## Database
* [ ] Should support postgreSQL  
