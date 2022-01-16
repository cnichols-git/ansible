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

You can over ride an /etc/ansible/ansible.cfg file if you make a local config file of the same name. Also ensure that if you specify an inventory file that you add one in this location also.

<pre>[defaults]  
inventory = inventory
private_key_file = ~/.ssh/ansible</pre>

/project/ansible.cfg  
/project/inventory  
/project/site.yml  
/project/roles/  
roles/update_os/main.yml
roles/software_install/main.yml  

