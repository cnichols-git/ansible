All Things Ansible!

Simple template for creating a play
```
- name: Install MariaDB on Ubuntu
  hosts: node1
  become: true
  tasks:
    - name: Update APT Package Cache
      apt: update_cache=yes force_apt_get=yes cache_valid_time=3600
    - name: Install MariaDB
      apt:
        name: mariadb-server
        state: present
```
```
- name: Host Basic Apache Website
  hosts: node1
  become: true
  tasks:
    - name: Install Apache
      apt:
        name: apache2
        state: present
    - name: Create HTML file
      template:
        src: index.html
        dest: /var/www/html/index.html
    - name: Restart Apache and enable on boot
      service:
        name: apache2
        state: restarted
        enabled: true
```
