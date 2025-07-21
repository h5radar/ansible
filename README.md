# H5Radar Ansible Installer

This repository contains Ansible playbooks and provisioning scripts to install and deploy the H5Radar platform.

H5Radar application consists of several modules. For an overview of the entire platform and its repositories, please see the [organization-level README](https://github.com/h5radar).

## Features

- Automated deployment of H5Radar web UI and backend services
- Configuration of SSL certificates (self-signed or Let's Encrypt)
- Support for reverse proxy setup (Nginx or Apache)
- Customizable inventory and environment parameters for flexible deployments

## How to install application

There are a few ways to install the application. The main difference relates to SSL certification: self-signed, Let's Encrypt, or external files.

## Requirements

- Ansible 2.9 or higher
- Target machines accessible via SSH with appropriate permissions
- DNS and network configuration depending on SSL setup

### Self-signed certificates

- Copy `inventory/development/` files to `inventory/production/`
- Edit `inventory/production/hosts` to set up IP addresses
- Run the command:
   ```bash
   ansible-playbook -v --diff --inventory inventory/production main.yml
   ```
### Let's Encrypt certificates

- TODO: Configure public IP and DNS settings required for Let's Encrypt
- Copy `inventory/development/` files to `inventory/production/`
- Edit `inventory/production/hosts` to set up IP addresses
- Run the command:
   ```bash
   ansible-playbook -v --diff --inventory inventory/production main.yml
   ```

## Resources

- [Website](https://www.h5radar.com)
- [Documentation](https://docs.h5radar.com)
- [Live Demo](https://app.h5radar.com)
- [Blog](https://blog.h5radar.com)

## Contributing

Contributions and issues are welcome. Please open pull requests or issues in this repository. For general discussions, roadmap input, and questions, please join our [organization Discussions](https://github.com/orgs/h5radar/discussions). We appreciate community involvement in shaping H5Radar!

## License

H5Radar Ansible Installer is licensed under the MIT License.

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
