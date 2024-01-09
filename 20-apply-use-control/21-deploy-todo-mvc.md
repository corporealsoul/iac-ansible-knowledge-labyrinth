### Install and Configure TodoMVC,


`[anup@rhel-92-104 ~]$ ansible all -m ping`

<br>

`[anup@rhel-92-104 ~]$ ansible-inventory --list`

<br>

`[anup@rhel-92-104 ~]$ cd /etc/ansible/playbook/`

`[anup@rhel-92-104 playbook]$ ls -ltr`

`[anup@rhel-92-104 playbook]$ mkdir templates`

`[anup@rhel-92-104 playbook]$ cd templates/`

`[anup@rhel-92-104 templates]$ sudo nano nginx_todomvc.conf.j2`

    server {
        listen 80;
        server_name 192.168.56.108;  # Replace with your domain name or IP address
    
        location / {
            root /var/www/todomvc;
            index index.html;
        }
    }

`[anup@rhel-92-104 templates]$ cd ..`

`[anup@rhel-92-104 playbook]$ sudo nano deploy-todomvc.yml `

    ---
    - name: Install and Configure TodoMVC
      hosts: worker
      become: yes
      tasks:
        - name: Update apt cache
          apt:
            update_cache: yes
    
        - name: Install Nginx
          apt:
            name: nginx
            state: present
    
        - name: Start Nginx service
          systemd:
            name: nginx
            state: started
            enabled: yes
    
        - name: Clone TodoMVC repository
          git:
            repo: https://github.com/tastejs/todomvc.git
            dest: /var/www/todomvc
            version: master
    
        - name: Create Nginx virtual host configuration
          template:
            src: nginx_todomvc.conf.j2
            dest: /etc/nginx/sites-available/todomvc
          notify:
            - Reload Nginx
    
        - name: Enable Nginx virtual host
          file:
            src: /etc/nginx/sites-available/todomvc
            dest: /etc/nginx/sites-enabled/todomvc
            state: link
          notify:
            - Reload Nginx
    
      handlers:
        - name: Reload Nginx
          systemd:
            name: nginx
            state: reloaded

`[anup@rhel-92-104 playbook]$ ansible-playbook deploy-todomvc.yml --syntax-check`

`[anup@rhel-92-104 playbook]$ ansible-playbook deploy-todomvc.yml --check`

`[anup@rhel-92-104 playbook]$ ansible-playbook deploy-todomvc.yml --ask-pass`

`anup@rhel-92-104 playbook]$ ansible-playbook deploy-todomvc.yml --ask-become-pass --check`

`[anup@rhel-92-104 playbook]$ ansible-playbook deploy-todomvc.yml --ask-become-pass`

`[anup@rhel-92-104 playbook]$ ansible-playbook deploy-todomvc.yml --ask-become-pass -vvv`

<br>

http://192.168.56.108/

<br>
