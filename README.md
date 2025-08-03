# H5Radar Ansible Installer

This repository contains Ansible playbooks and provisioning scripts to install and deploy the H5Radar platform.

H5Radar application consists of several modules. For an overview of the entire platform and its repositories, please see the [organization-level README](https://github.com/h5radar).

## Features

- Automated deployment of H5Radar web UI and backend services
- Customizable inventory and environment parameters for flexible deployments
- Configuration of SSL certificates (self-signed or Let's Encrypt via HTTP verification)
- Support for reverse proxy setup (Nginx or Apache)
- Built-in Keycloak deployment or integration with an external Keycloak instance

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

## Appendix 1: Useful commands

- run linter by command: ansible-lint ./main.yml
