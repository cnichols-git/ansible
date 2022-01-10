## Ansible ##

First install ansible on a management server/workstation  

RHEL:  
`#dnf install ansible`

Ubuntu:  
`# sudo apt update`  
`# sudo apt install software-properties-common`  
`# sudo apt-add-repository --yes --update ppa:ansible/ansible`  
`# sudo apt install ansible`

[How to set up SSH key sharing](https://github.com/cnichols-git/ansible/tree/master/notes/ssh_setup.md)


**Run a playbook locally**
- ansible-playbook --connection=local playbook.yml
	if you run this as is it will run on all systems in /etc/ansible/hosts

