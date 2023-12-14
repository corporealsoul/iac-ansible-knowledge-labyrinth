### System configuration,

**Should be able to ping each other,**

`[anup@rhel-92-32 ~]$ sudo nano /etc/hosts`

    127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
    ::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
    
    192.168.56.4    rhel-92-04
    192.168.56.8    ubuntu-22042-08
    192.168.56.32   rhel-92-32

`[anup@rhel-92-04 ~]$ ping rhel-92-32`

<br>

**Should be able to ssh each other,**

`[anup@rhel-92-04 ~]$ ssh-keygen -t rsa -b 4096`

    Enter passphrase (empty for no passphrase): 0%!oS3%EDR9C6

`[anup@rhel-92-32 ~]$ ssh-copy-id anup@192.168.56.8`

`[anup@rhel-92-32 ~]$ ssh-copy-id anup@192.168.56.4`

`[anup@rhel-92-32 ~]$ ssh ubuntu-22042-08`

`[anup@rhel-92-32 ~]$ ssh rhel-92-04`


<br>

Ensure your SSH agent is running:
eval "$(ssh-agent -s)"

Add your private key to the SSH agent:
ssh-add ~/.ssh/id_rsa

Check that the key has been added:
ssh-add -l

After performing these steps, try SSH-ing into the remote server again:
ssh anup@192.168.56.5


<br>

**User should be added to the visudo,**

`[anup@rhel-92-32 ~]$ sudo visudo`

    root 	ALL=(ALL) 	ALL 
    anup 	ALL=(ALL) 	NOPASSWD:ALL

<br>

**sshpass should be present and running,**

`[anup@rhel-92-32 ~]$ yum install sshpass`

<br>

**Git should present,**

`[anup@rhel-92-32 ~]$ git --version`

<br>

**Python should present,**

`[anup@rhel-92-32 ~]$ python3 -V`

<br>

**PIP should present,**

`[anup@rhel-92-32 ~]$ sudo dnf install python3-pip`

`[anup@rhel-92-32 ~]$ python3 -m pip install --user pipenv`

`[anup@rhel-92-32 ~]$ python3 -m pip -V`

<br>

`[anup@rhel-92-32 ~]$ sudo apt-get install python3-pip`

`[anup@rhel-92-32 ~]$ python3 -m pip -V`

<br>

`[anup@rhel-92-104 ~]$ python3 -m pip install --user pipx`

`[anup@rhel-92-104 ~]$ pipx --version`

<br>

