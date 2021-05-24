## Ansible

First install ansible on a management server/workstation

**You need python, of course

RHEL:
# dnf install ansible

Ubuntu:
# sudo apt update
# sudo apt install software-properties-common
# sudo apt-add-repository --yes --update ppa:ansible/ansible
# sudo apt install ansible

Generate an SSH key
# ssh -keygen

Copy key to the server
# ssh-copy-id <name of host or ip> 

If you change the location of the ansible config files ensure that you have changed the ansible.cfg to point to the correct location.

ex. #inventory      = /etc/ansible/hosts (you may choose to have = /scratch/automation/ansible_hosts)

idempotent - element of a set which is unchanged in value when multiplied or otherwise operated on by itself.
-b - become
-m - module
-a - argument
-i - defines the non default inventory -i inv <name of inventory>
-e - 

inventories - the list of host that are in a file that you specify
service module - 
plays - a series of steps to be performed on a host or series of host
Variables - 
Facts - detailed information about a play book
you can use filters when running facts
ex. 
ansible <hostname> -m setup -a filter=*ipv4* | ansible <hostname> -m setup -a filter=*hostname*
gather_facts: no - this will disable fact and no longer auto gather facts

## Adhoc Commands

# how to get past a password prompt
ansible all -m ping --ask-pass 
ansible -m ping all

# Ping a specific host
ansible ansible-client -m ping

# how to get past a password prompt
ansible-playbook myplaybook.yml --ask-pass

# prints host name of all host in the hosts folder 
ansible -m shell -a 'hostname' all

not sure what I am doing here?
ansible <hostname> -m setup
ansible <hostname> -m setup | less



starting httpd - ansible <hostname> -b -m service -a “name=httpd state=”started”

Troubleshoot and Debug
msg - a message that is printed to stdout
var - a variable whose content is printed to stdout

ex.
-debug:
 msg: System “”{{ inventory_hostname has uuid {{ asible_product_uuid }}””

Handlers

-name: template configuration file
 template:
	src: foo.conf
	dest: /etc/foo/conf
 notify:
 -restart memcached 

handlers:
 -name: restart httpd
 service: 

A handler is only going to run if the notify option is called


List of all the thing to get start, that I always refference
=======
List of all the things I need to get started with some lab fun/learning

**Run a playbook locally**
- ansible-playbook --connection=local playbook.yml
	if you run this as is it will run on all systems in /etc/ansible/hosts

**To run a playbook without the --connection flag**

you can create a variable in the /etc/ansible/hosts file

[local]

127.0.0.1

**Generating ssh keys**
- create the public and private keys ssh-keygen -t rsa 
