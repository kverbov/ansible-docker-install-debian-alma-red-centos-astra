docker-install 
=========

Installing docker / docker-compose and its dependencies on a new server.

Role variables
------------
Description and examples of variables are given in the defaults/main.yml file

Deployment
--------------

In order to deploy docker on a new server, you need to:

Determine the installation method in the "docker_install_offline_mode" variable. If this is offline mode, then download the packages and specify the path to the directory in the "docker_dist_name" variable and the base directory "docker_dist_path" If this is online mode, then specify the paths to the online repository and keys in the variables depending on the version of the packages:

RPM packages: docker_rpm_gpg_url docker_rpm_repo_string

DEB packages: docker_deb_key_url docker_deb_repo_string

Using templates
------------
It is possible to use templates. In order for a file to be considered a template, you need to add .j2 to its extension, for example: docker-compose.yml -> docker-compose.yml.j2. During the generation of final files, the .j2 extension will be discarded. The following templates are provided in this role:

10sandbox.j2 - config file for apt-manager
yum.conf.j2 - config file for yum-manager
docker-online.repo.j2 - config file for online repositories
docker-repository.list.j2 - config file for offline repositories
docker.repo.j2 - config file for remote repository

Launch
------------
To launch, it is recommended to specify the version of the python interpreter installed on the target host: ansible-playbook -i ~/hosts.txt ~/main.yml -vv --extra-vars 'ansible_python_interpreter=/usr/bin/python3.5'
