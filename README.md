## Supported tags and respective `Dockerfile` links
- [`centos` (*centos-epel/Dockerfile*)](https://github.com/kostasns/ansible-docker/blob/master/centos-epel/Dockerfile)
- [`alpine` (*alpine/Dockerfile*)](https://github.com/kostasns/ansible-docker/blob/master/alpine/Dockerfile)

## How to use this image
### Launching the container
```
$ docker run -it --rm -v $(pwd):/ansible kostasns/ansible:**<tag>** <ansible_command>
```

#### With common roles
More info on [roles path variable](http://docs.ansible.com/ansible/intro_configuration.html#roles-path) 
```
docker run -it --rm -v $(pwd):/ansible -v *local_roles_path*:/ansible/common_roles kostasns/ansible:**<tag>** <ansible_command> 
```

### Using aliases
#### Bash/Git
```
alias ansible='docker run -it --rm -v $(pwd):/ansible kostasns/ansible:**<tag>** ansible'
alias ansible-playbook='docker run -it --rm -v $(pwd):/ansible kostasns/ansible:**<tag>** ansible-playbook'
alias ansible-vault='docker run -it --rm -v $(pwd):/ansible kostasns/ansible:**<tag>** ansible-vault'
```

#### PowerShell
```
function ansible { & docker run -it --rm -v "$(pwd):/ansible" "kostasns/ansible:**<tag>**" ansible }
function ansible-playbook { & docker run -it --rm -v "$(pwd):/ansible" "kostasns/ansible:**<tag>**" ansible-playbook }
function ansible-vault { & docker run -it --rm -v "$(pwd):/ansible" "kostasns/ansible:**<tag>**" ansible-vault }
```

### CoreOS Bootstrap
Container comes with [coreos-bootstrap](https://github.com/defunctzombie/ansible-coreos-bootstrap) installed
