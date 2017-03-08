[![License](https://img.shields.io/badge/license-Apache%202-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0)
[![Build Status](https://travis-ci.org/grycap/ansible-role-docker-swarm.svg?branch=master)](https://travis-ci.org/grycap/ansible-role-docker-swarm)

Docker Swarm Role
===================

Install Docker swarm cluster (recipe for EC3)

Role Variables
--------------

The variables that can be passed to this role and a brief description about them are as follows.

	# Type of node front or wn
	swarn_type_of_node: "front"
	# IP address of the swarm manager
	swarn_manager_address: "{{ ansible_default_ipv4.address }}"
	# swarm manager port
	swarn_manager_port: 2377
	# set docker_opts for the docker role
	swarm_docker_opts: "-H unix:///var/run/docker.sock  -H tcp://0.0.0.0:2375 --dns 8.8.8.8 --dns 8.8.4.4"

Example Playbooks
----------------

```
  - hosts: manager
    roles:
    - { role: 'grycap.swarm' }
```

```
  - hosts: worker
    roles:
    - { role: 'grycap.swarm', swarn_type_of_node: 'wn', swarn_manager_address: '10.0.0.1' }
```

Contributing to the role
========================
In order to keep the code clean, pushing changes to the master branch has been disabled. If you want to contribute, you have to create a branch, upload your changes and then create a pull request.
Thanks
