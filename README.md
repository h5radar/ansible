# Ansible
Ansible installer for h5radar application. Demo available at https://app.h5radar.com.

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

## Windows environment

```
# Setup apt env
DEBIAN_FRONTEND=noninteractive
NEEDRESTART_MODE=l
sudo apt-get update && sudo apt-get -y install python3-venv

# Setup python env
python3 -m venv --upgrade-deps .venv && source .venv/bin/activate
pip install --requirement requirements.txt

# Setup ansible env
export ANSIBLE_CONFIG=ansible.cfg
ansible-galaxy install -r requirements.yml

vagrant up
```

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
