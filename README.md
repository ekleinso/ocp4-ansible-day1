# ocp4-ansible-day1
This is an ansible repository that configures a bastion/day1 host for installing OpenShift. 

## Prerequisite
A workstation or VM with RHEL 8 and Ansible installed. 
Minimum specification
- 4 vCPU
- 8GB RAM
- 200GB Disk

## Install instructions
To install in Ansible 2.10 or greater use ansible-galaxy and install directly from git.
```shell
ansible-galaxy collection install https://github.com/ekleinso/ocp4-ansible-day1.git
```

For versions less than 2.10
```shell
git clone https://github.com/ekleinso/ocp4-ansible-day1.git
cd ocp4-ansible-day1
ansible-galaxy collection build
ansible-galaxy collection install -f ./ibmce-ocp_day1-1.0.0.tar.gz 
```

Create a playbook to invoke the Ansible roles
```yaml
---
- name: Deploy day1
  gather_facts: yes
  hosts: localhost

  roles:
   - ibmce.ocp_day1.os_prereq
   - ibmce.ocp_day1.httpd
   - ibmce.ocp_day1.ocp_tools
   - ibmce.ocp_day1.mirror_registry
   - ibmce.ocp_day1.oai
```
