## Ansible ##

First install ansible on a management server/workstation  

RHEL:  
`#dnf install ansible`

Ubuntu:  
`# sudo apt update`  
`# sudo apt install software-properties-common`  
`# sudo apt-add-repository --yes --update ppa:ansible/ansible`  
`# sudo apt install ansible`

Links to the following :  

[Set up SSH key sharing](https://github.com/cnichols-git/ansible/tree/master/notes/ssh_setup.md)  
[Ad Hoc Commands](https://github.com/cnichols-git/ansible/blob/master/notes/adhoc_commands.md)  
[Modules](https://github.com/cnichols-git/ansible/blob/master/notes/modules.md)


**Run a playbook locally**
- ansible-playbook --connection=local playbook.yml
	if you run this as is it will run on all systems in /etc/ansible/hosts  