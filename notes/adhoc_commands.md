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

ansible all -m yum -a update_cache=true --become --ask-become-pass