Ansible Files,


Ansible Logs,


Ansible,
Ping
[anup@c9-35-controller ~]$ ansible localhost -m ping
[root@192 ~]# ansible -i /etc/ansible/hosts webservers -m ping
[root@192 ~]# ansible all -m ping

[root@192 ~]# ansible -i /etc/ansible/hosts webservers -m ping

List hosts,
[root@192 ~]# ansible all --list-hosts

[root@192 ~]# ansible webservers --list-hosts

[root@192 ~]# ansible webservers[0] --list-hosts

[root@192 ~]# ansible webservers[1] --list-hosts

[root@192 ~]# ansible webservers[2:3] --list-hosts


Ad-hoc and modules commands -

[root@192 ~]# ansible webservers -a "ls"

[root@192 ~]# ansible webservers -a "touch ansible_guide"

[root@192 ~]# ansible all -a "touch ansible_commands"

Managing packages -

[root@192 ~]# ansible webservers -a "dnf install httpd -y"

[root@192 ~]# ansible webservers -a "sudo dnf install httpd -y"

[root@192 ~]# ansible webservers -ba "dnf install httpd -y"

Module commands -

Gathering facts - Facts represent discovered variables about a system.

[root@192 ~]# ansible all -m ansible.builtin.setup

[root@192 ~]# ansible webservers -m ansible.builtin.setup

[root@192 ~]# ansible webservers[1] -m ansible.builtin.setup

Managing files-

[root@192 ~]# ansible webservers -m ansible.builtin.file -a "dest=/home/anup/ansible_file state=touch"

Dry run :

[root@192 anup]# ansible-playbook ansiplay.yml --check
[root@192 anup]# ansible-playbook ansiplay.yml --check

[root@192 anup]# ansible-playbook ansiplay.yml

[root@192 anup]# ansible-playbook ansiplay.yml -f 10


Ansible Galaxy,



ANsible tower,

https://docs.ansible.com/ansible-tower/2.2.2/html/installandreference/requirements_refguide.html 

https://ny55.blogspot.com/2020/07/how-to-install-and-configure-ansible.html 

https://computingforgeeks.com/install-and-configure-ansible-tower-on-centos-rhel/ 

https://www.redhat.com/en/technologies/management/ansible/try-it

Ansible AWX -

Ansible AWX -




Ansible Roles,



