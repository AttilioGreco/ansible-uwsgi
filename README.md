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
