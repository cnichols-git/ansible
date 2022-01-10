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