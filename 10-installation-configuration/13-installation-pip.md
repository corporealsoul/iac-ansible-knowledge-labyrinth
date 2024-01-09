Installing Ansible, **PIP Installation,** https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#pip-install

`[anup@rhel-92-104 ~]$ sudo dnf install python3`

`[anup@rhel-92-104 ~]$ python3 --version`

<br>

`[anup@rhel-92-104 ~]$ wget https://bootstrap.pypa.io/get-pip.py`

`[anup@rhel-92-104 ~]$ python3 ./get-pip.py`

`[anup@rhel-92-104 ~]$ python3 -m pip -V`

`[anup@rhel-92-104 ~]$ pip --version`

<br>

`[anup@rhel-92-104 ~]$ python3 -m pip install --user ansible`

`[anup@rhel-92-104 ~]$ ansible --version`

`[anup@rhel-92-104 ~]$ python3 -m pip show ansible`

<br>

`[anup@rhel-92-104 ~]$ python3 -m pip install --upgrade --user ansible`

<br>

### Generating a sample ansible.cfg file,

**You can generate a fully commented-out example ansible.cfg file, for example:**

`[anup@rhel-92-104 ~]$ ansible-config init --disabled > ansible.cfg`


**You can also have a more complete file that includes existing plugins:**

`[anup@rhel-92-104 ~]$ ansible-config init --disabled -t all > ansible.cfg`

<br>

`[anup@rhel-92-104 ~]$ ls -ltr ~/ansible.cfg`

**or,**

`[anup@rhel-92-104 ~]$ ls -ltr /etc/ansible/ansible.cfg`

<br>

### Creating a working directory,

`[anup@rhel-92-104 ~]$ ls -ltr /etc/ansible`

`[anup@rhel-92-104 ~]$ sudo mkdir /etc/ansible`

`[anup@rhel-92-104 ~]$ sudo nano /etc/ansible/hosts`

    [controller]
    192.168.56.104  ansible_ssh_user=anup   ansible_ssh_pass= # Host address, user_name and password
    
    [worker]
    192.168.56.108  ansible_ssh_user=anup   ansible_ssh_pass= # Host address, user_name and password

`[anup@rhel-92-104 ~]$ ansible-inventory --list`

<br>

### Checking communication,

`[anup@rhel-92-104 ~]$ ansible localhost -m ping`

`[anup@rhel-92-104 ~]$ ansible all -m ping`

`[anup@rhel-92-104 ~]$ ansible controller -m ping`

`[anup@rhel-92-104 ~]$ ansible worker -m ping`

`[anup@rhel-92-104 ~]$ ansible-inventory --list`

`[anup@rhel-92-104 ~]$ ansible 192.168.56.108 -m ping`

`[anup@rhel-92-104 playbook]$ ansible -i /etc/ansible/hosts controller -m ping`

<br>

### Run a playbook,

`[anup@rhel-92-104 ~]$ cd /etc/ansible/`

`[anup@rhel-92-104 ansible]$ sudo mkdir playbook`

`[anup@rhel-92-104 ansible]$ cd playbook/`

`[anup@rhel-92-104 playbook]$ sudo nano gather_facts.yml`

    ---
    - name: Gathering Facts
      hosts: all
    #  hosts: controller
    #  hosts: worker
      gather_facts: yes
    ...

`[anup@rhel-92-104 playbook]$ ansible-playbook gather_facts.yml --check`

`[anup@rhel-92-104 playbook]$ ansible-playbook -i /etc/ansible/hosts gather_facts.yml --check`

`[anup@rhel-92-104 playbook]$ ansible-playbook -l controller gather_facts.yml --check`

<br>
