- Variables
  - NAME="Miftahul"
  - VARIABLE_NAME="VALUE"
  - echo $NAME
  - echo NAME (wrong)
  - echo ${NAME}
  - echo ${NAME:0:5}
  - env
  - export PATH="/usr/games:$PATH"
  - export myvar="value"
  - unset myvar
- SSH, SCP & rsync
  - sudo netstat -tulpn
  - systemctl status ssh
  - sudo apt install openssh-server
  - ip a
  - /etc/ssh/sshd_config
    - PermitRootLogin no
    - PasswordAuthentication no
  - rsync -avz --dry-run
  - scp
- journalctl
  - -u apache
  - -f
- !!
- $! $? $$ $# $0
- Systemd
  - systemctl start stop enable disable restart
- User, Group & Permission Management
  - groups
  - adduser
  - su - username
  - passwd username
  - logout
  - userdel -r username
  - groupadd groupname
  - groupdel -r groupname
  - sudo usermod -aG groupname username
  - sudo gpasswd -d username groupname
  - exit logout sudo su -
- history
  - !number
- $?

- who
- w
- last
- lastb

- id
- chown
- chmod -> chmod new_permission file_name -> To change a file's permissions, you either need to own the file or log in as the root user.
- stat

## chown
There are three different ways the chown command can be executed. The first method is used to change just the user owner of the file.
chown user /path/to/file
For example, if the root user wanted to change the user ownership of the filetest1 file to the user jane, then the following command could be executed:
root@localhost:~# chown jane /tmp/filetest1
root@localhost:~# ls -l /tmp/filetest1
-rw-rw-r-- 1 jane sysadmin 0 Dec 19 18:44 /tmp/filetest1


The second method is to change both the user and the group; this also requires root privileges. To accomplish this, you separate the user and group by either a colon or a period character. For example:
chown user:group /path/to/file
chown user.group /path/to/file


root@localhost:~# chown jane:users /tmp/filetest2
root@localhost:~# ls -l /tmp/filetest2
-rw-r--r-- 1 jane users 0 Dec 19 18:53 /tmp/filetest2


If a user doesn't have root privileges, they can use the third method to change the group owner of a file just like the chgrp command. To use chown only to change the group ownership of the file, use a colon or a period as a prefix to the group name:
chown :group /path/to/file
chown .group /path/to/file


jane@localhost:~$ chown .users /tmp/filetest1
jane@localhost:~$ ls -l /tmp/filetest1
-rw-rw-r-- 1 jane users 0 Dec 19 18:44 /tmp/filetest1


