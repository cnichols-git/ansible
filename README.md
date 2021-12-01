## Ansible ##

First install ansible on a management server/workstation  

RHEL:  
`#dnf install ansible`

Ubuntu:  
`# sudo apt update`  
`# sudo apt install software-properties-common`  
`# sudo apt-add-repository --yes --update ppa:ansible/ansible`  
`# sudo apt install ansible`

Generate an SSH key
`# ssh -keygen`

Copy key to the server
`ssh-copy-id <name of host or ip>`

If you change the location of the ansible config files ensure that you have changed the ansible.cfg to point to the correct location.

`ex. #inventory      = /etc/ansible/hosts (you may choose to have = /scratch/automation/ansible_hosts)`

## Adhoc Commands

**how to get past a password prompt**  
* ansible all -m ping --ask-pass 
* ansible -m ping all

**Ping a specific host**  
* ansible ansible-client -m ping

**how to get past a password prompt**  
* ansible-playbook myplaybook.yml --ask-pass

**prints host name of all host in the hosts folder**  
* ansible -m shell -a 'hostname' all

starting httpd - ansible <hostname> -b -m service -a “name=httpd state=”started”  

Troubleshoot and Debug
msg - a message that is printed to stdout
var - a variable whose content is printed to stdout

ex.
-debug:
 msg: System “”{{ inventory_hostname has uuid {{ asible_product_uuid }}””

**Run a playbook locally**
- ansible-playbook --connection=local playbook.yml
	if you run this as is it will run on all systems in /etc/ansible/hosts

**To run a playbook without the --connection flag**

you can create a variable in the /etc/ansible/hosts file

[local]

127.0.0.1

**Generating ssh keys**
- create the public and private keys ssh-keygen -t rsa 




## Modules

- apt/yum
- copy
- file
- get_url
- git
- ping
- debug
- service
- syncronize
- template
- uri
- user
- wait_for
- asset

module < yum >  

- name: install the 'Gnome desktop' environment group  
  yum:  
    name: "@^gnome-desktop-environment"  
    state: present  

- name: Install a list of packages  
  yum:  
    name:  
      - git 
      - postgresql  
      - postgresql-server  
    state: present  

- name: upgrade all packages
  yum:
    name: '*'
    state: latest

## Template

---
- name: play name  
  hosts: web  
  vars: 
    http_port:80
  remote_user: root

tasks: 
- name:
  yum: pkg=httpd state=latest
- name:
  template: src=/location/of/source/file dest=/etc/httpd.conf
- name:
  service: name=httpd state=started  
### Direcroty structure for roles
site.yml
webservers.yml
fooservers.yml
roles/  
   common/  
     tasks/  
     handlers/  
     files/
     templates/
     vars/
     defaults/
     meta/
   webservers/
     tasks/
     defaults/
     meta/`  
	
Example:  
roles/  
&nbsp;&nbsp;&nbsp; common_software/  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  files/  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  tasks/  
or  
&nbsp;&nbsp;&nbsp; browser-install  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  files/  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;	google-install.yaml  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;    tasks/  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  main.yaml  
