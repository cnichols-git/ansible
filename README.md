## Ansible

List of all the things I need to get started with some lab fun/learning

**Run a playbook locally**
- ansible-playbook playbook.yml --connection=local

**To run a playbook without the --connection flag**

you can create a variable in the /etc/ansible/hosts file

[local]

127.0.0.1

**Generating ssh keys**
- create the public and private keys ssh-keygen -t rsa 
- ssh-copy-id \<name of system\>

**Next**
