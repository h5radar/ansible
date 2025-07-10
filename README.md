# Ansible
Ansible installer for h5radar application

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

# Development
```
# Setup python env
DEBIAN_FRONTEND=noninteractive
NEEDRESTART_MODE=l
sudo apt-get update && sudo apt-get -y install python3-venv
python3 -m venv --upgrade-deps .venv && source .venv/bin/activate
pip install --requirement pip_requirements.txt

# Setup ansible env
export ANSIBLE_CONFIG=ansible.cfg
ansible-galaxy install -r galaxy_requirements.yml

# deploy via Vagrant or
ansible-playbook deploy.yml --ask-become-pass --extra-vars "hostname=somename" [--tags basic]

# deploy via ansible
ansible-inventory --graph
time ansible-playbook main.yml
```

