Ansible Role: {{cookiecutter.service_name}} 
======================================

[![Build Status](https://travis-ci.org/entercloudsuite/{{cookiecutter.role_name}}.svg?branch=master)](https://travis-ci.org/entercloudsuite/{{cookiecutter.role_name}})
[![Galaxy](https://img.shields.io/badge/galaxy-entercloudsuite.{{cookiecutter.service_name}}-blue.svg?style=flat-square)](https://galaxy.ansible.com/entercloudsuite/{{cookiecutter.service_name}})  

Installs {{cookiecutter.service_name}} on Ubuntu 16.04 (Xenial)

## Requirements

This role requires Ansible {{cookiecutter.ansible_min_version}} or higher.

## Role Variables

The role defines most of its variables in `defaults/main.yml`:

## Example Playbook

Run with default vars:

    - hosts: all
      roles:
        - { role: {{cookiecutter.role_name}} }

## Testing

Tests are performed using [Molecule](http://molecule.readthedocs.org/en/latest/).

Install Molecule or use `docker-compose run --rm molecule` to run a local Docker container, based on the [enterclousuite/molecule](https://hub.docker.com/r/fminzoni/molecule/) project, from where you can use `molecule`.

1. Run `molecule create` to start the target Docker container on your local engine.  
2. Use `molecule login` to log in to the running container.  
3. Edit the role files.  
4. Add other required roles (external) in the molecule/default/requirements.yml file.  
5. Edit the molecule/default/playbook.yml.  
6. Define infra tests under the molecule/default/tests folder using the goos verifier.  
7. When ready, use `molecule converge` to run the Ansible Playbook and `molecule verify` to execute the test suite.  
Note that the converge process starts performing a syntax check of the role.  
Destroy the Docker container with the command `molecule destroy`.   

To run all the steps with just one command, run `molecule test`. 

In order to run the role targeting a VM, use the playbook_deploy.yml file for example with the following command: `ansible-playbook {{cookiecutter.role_name}}/molecule/default/playbook_deploy.yml -i VM_IP_OR_FQDN, -u ubuntu --private-key private.pem`.  

# ansible-uwsgi | absible role for install uWsgi
Tested on Ubuntu -  Centos
## Role variables
| Name | Description | Default Value |
| --- | --- | --- |
|uwsgi_version:| Softwere Version | Lastes
|environmentFile:|  | /etc/sysconfig/uwsgi|
|uwsgi_bin_path: | Path uwsgi Binary file | /sbin|
|uwsgi_run: | Unix Data socket | /run/uwsgi|
|uwsgi_run_stats:| Unix stats socket | /run/uwsgi/stat|
|uwsgi_log_path:| Log | /var/log/uwsgi|
|uwsgi_user:| uWsgi User |nginx|
|uwsgi_group:| uWsgi Group | nginx|
|uwsgi_ini_path:| Main uWsgi Config file | /etc|

For python deply is recommended use vrtualenv.
Usualy the virtualenv home is specified in venv role variable, in this case set this variable as the variable se in your venv role.

| Name | Description | Default Value |
| --- | --- | --- |
|venv_home | Virtual Env Path | /usr/venv |

## Playbook Example
``` yml
- name: run uwsgi roles
  hosts: all
  roles:
    - role: ansible-uwsgi
```
