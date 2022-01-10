## Notes for learning ##
### This will update frequently ###

**Create SSH key for a normal user, maybe**   

keys are stored in the .ssh dir  
generate a key with the command  
<code># ssh-keygen -C "ansible_key"</code>  
the -C will allow you to add a comment  

**Make an Ansible key and cp to all servers**  
ssh-copy-id <name of host or ip>  

ssh-keygen -C "ansible"  
check the path to the key and change it.  

<pre>chris@office:~/.ssh$ ssh-keygen -C "ansible"
Generating public/private rsa key pair.
Enter file in which to save the key (/home/chris/.ssh/id_rsa): /home/chris/.ssh/ansible
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/chris/.ssh/ansible
Your public key has been saved in /home/chris/.ssh/ansible.pub
</pre>  

Do not use a passphrase for this key  

<pre>chris@office:~/.ssh$ ssh-copy-id -i ~/.ssh/ansible.pub 10.0.0.30
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/chris/.ssh/ansible.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
chris@10.0.0.30's password: 

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh '10.0.0.30'"
and check to make sure that only the key(s) you wanted were added.
</pre>

cp this key to all servers_nodes  

<code># ssh-copy-id -i ~/.ssh/ansible.pub 10.0.0.30</code>  

On the server_nodes you can see the authorized keys in the path  
/home/user/.ssh/  

##