### Ansible Files,
<br>


### Ansible Logs,
<br>


### Ansible,
<br>

**Ping,**

`[anup@rhel-92-104 ~]$ ansible localhost -m ping`

`[anup@rhel-92-104 ~]$ ansible -i /etc/ansible/hosts webservers -m ping`

`[anup@rhel-92-104 ~]$ ansible all -m ping`

`[anup@rhel-92-104 ~]$ ansible -i /etc/ansible/hosts webservers -m ping`

<br>


**List hosts,**

`[anup@rhel-92-104 ~]$ ansible all --list-hosts`

`[anup@rhel-92-104 ~]$ ansible webservers --list-hosts`

`[anup@rhel-92-104 ~]$ ansible webservers[0] --list-hosts`

`[anup@rhel-92-104 ~]$ ansible webservers[1] --list-hosts`

`[anup@rhel-92-104 ~]$ ansible webservers[2:3] --list-hosts`

<br>


**Ad-hoc and modules commands,**

`[anup@rhel-92-104 ~]$ ansible webservers -a "ls"`

`[anup@rhel-92-104 ~]$ ansible webservers -a "touch ansible_guide"`

`[anup@rhel-92-104 ~]$ ansible all -a "touch ansible_commands"`

<br>


**Managing packages,**

`[anup@rhel-92-104 ~]$ ansible webservers -a "dnf install httpd -y"`

`[anup@rhel-92-104 ~]$ ansible webservers -a "sudo dnf install httpd -y"`

`[anup@rhel-92-104 ~]$ ansible webservers -ba "dnf install httpd -y"`

<br>


**Module commands,**

`[anup@rhel-92-104 ~]$ ansible all -m ansible.builtin.setup`

`[anup@rhel-92-104 ~]$ ansible webservers -m ansible.builtin.setup`

`[anup@rhel-92-104 ~]$ ansible webservers[1] -m ansible.builtin.setup`

<br>


**Managing files,**

`[anup@rhel-92-104 ~]$ ansible webservers -m ansible.builtin.file -a "dest=/home/anup/ansible_file state=touch"`

<br>


**Dry run,**
`[anup@rhel-92-104 ~]$ ansible-playbook ansiplay.yml --check`

`[anup@rhel-92-104 ~]$ ansible-playbook ansiplay.yml --check`

`[anup@rhel-92-104 ~]$ ansible-playbook ansiplay.yml`

`[anup@rhel-92-104 ~]$ ansible-playbook ansiplay.yml -f 10`

<br>


**Ansible Galaxy,**

<br>


**Ansible Roles,**

<br>


**Ansible tower,**

https://docs.ansible.com/ansible-tower/2.2.2/html/installandreference/requirements_refguide.html 

https://ny55.blogspot.com/2020/07/how-to-install-and-configure-ansible.html 

https://computingforgeeks.com/install-and-configure-ansible-tower-on-centos-rhel/ 

https://www.redhat.com/en/technologies/management/ansible/try-it

<br>


**Ansible AWX -**

<br>

**Ansible AWX -**
<br>

<br>
