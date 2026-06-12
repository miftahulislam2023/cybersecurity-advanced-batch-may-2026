# Class 7

## Today's Topic
- The Linux command line for beginners

## Reference
- [ubuntu_cli_cheat_sheet_2025](https://assets.ubuntu.com/v1/d00791ae-ubuntu_cli_cheat_sheet_2025.pdf)
- [The Linux command line for beginners](https://ubuntu.com/desktop/docs/en/latest/tutorial/the-linux-command-line-for-beginners/)
- [Termux](https://f-droid.org/repo/com.termux_1022.apk)

## Commands
1. `pwd`
2. `cd`
3. `ls -lsah`
4. `clear` or ctrl + l
5. `mkdir <directory_name>`
6. `rmdir <directory_name>`
7. `whoami`
8. `mkdir -p dir1/dir2/dir3`

## Important Directories
1. / -> root directory
2. ~ -> user home directory


## Some important signs and symbols
```
1. - hyphen, dash
2. ` back tick
3. ~ tilde
4. ! exclamation mark
5. $ dollar sign
6. ^ caret
7. & ampersand
8. * asterisk
9. () parenthesis, first bracket
10. {} curly braces, second bracket
11. [] square bracket, third bracket
12. <> angle bracket
13. _ underscore
14. / forward slash
15. \ backslash
16. '' single quotation mark
17. "" double quotation mark
18. ? question mark
19. | pipe character
20. ; semicolon
21. : colon
22. , comma
23. . dot
24. -> arrow
25. % percentage, modulus
26. # hash
```


```bash
miftah@miftahcoding:~$ pwd
/home/miftah
miftah@miftahcoding:~$ cd /
miftah@miftahcoding:/$ pwd
/
miftah@miftahcoding:/$ ls
bin   cdrom  etc   lib         media  opt   root  sbin  srv       sys  usr
boot  dev    home  lost+found  mnt    proc  run   snap  swap.img  tmp  var
miftah@miftahcoding:/$ cd home/
miftah@miftahcoding:/home$ pwd
/home
miftah@miftahcoding:/home$ ls
miftah
miftah@miftahcoding:/home$ cd miftah/
miftah@miftahcoding:~$ ls
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos  snap
miftah@miftahcoding:~$ pwd
/home/miftah
miftah@miftahcoding:~$ ls 
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos  snap
miftah@miftahcoding:~$ ls -lsah
total 72K
4.0K drwxr-x--- 15 miftah miftah 4.0K Jun  6 18:49 .
4.0K drwxr-xr-x  3 root   root   4.0K Jun  6 18:43 ..
4.0K -rw-r--r--  1 miftah miftah  220 Feb 13 18:16 .bash_logout
4.0K -rw-r--r--  1 miftah miftah 3.7K Feb 13 18:16 .bashrc
4.0K drwx------ 12 miftah miftah 4.0K Jun 12 21:38 .cache
4.0K drwx------ 14 miftah miftah 4.0K Jun 12 21:34 .config
4.0K drwx------  4 miftah miftah 4.0K Jun  6 18:49 .local
4.0K -rw-r--r--  1 miftah miftah  807 Feb 13 18:16 .profile
4.0K drwx------  2 miftah miftah 4.0K Jun  6 18:48 .ssh
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Desktop
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Documents
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Downloads
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Music
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Pictures
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Public
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Templates
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Videos
4.0K drwx------  5 miftah miftah 4.0K Jun  6 18:51 snap
miftah@miftahcoding:~$ cd ..
miftah@miftahcoding:/home$ cd .
miftah@miftahcoding:/home$ cd ..
miftah@miftahcoding:/$ ls
bin   cdrom  etc   lib         media  opt   root  sbin  srv       sys  usr
boot  dev    home  lost+found  mnt    proc  run   snap  swap.img  tmp  var
miftah@miftahcoding:/$ cd home/miftah/
miftah@miftahcoding:~$ pwd
/home/miftah
miftah@miftahcoding:~$ cd ..
miftah@miftahcoding:/home$ ls
miftah
miftah@miftahcoding:/home$ mkdir
error: the following required arguments were not provided:
  <dirs>...

Usage: mkdir [OPTION]... DIRECTORY...

For more information, try '--help'.
miftah@miftahcoding:/home$ mkdir imran
mkdir: Permission denied
miftah@miftahcoding:/home$ ls -lsah
total 12K
4.0K drwxr-xr-x  3 root   root   4.0K Jun  6 18:43 .
4.0K drwxr-xr-x 20 root   root   4.0K Jun  6 18:42 ..
4.0K drwxr-x--- 15 miftah miftah 4.0K Jun  6 18:49 miftah
miftah@miftahcoding:/home$ cd miftah/
miftah@miftahcoding:~$ ls
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos  snap
miftah@miftahcoding:~$ cd Do
Documents/ Downloads/ 
miftah@miftahcoding:~$ cd Do
Documents/ Downloads/ 
miftah@miftahcoding:~$ cd Downloads/
miftah@miftahcoding:~/Downloads$ ls
miftah@miftahcoding:~/Downloads$ mkdir imran robi
miftah@miftahcoding:~/Downloads$ ls
imran  robi
miftah@miftahcoding:~/Downloads$ rmdir imran/
miftah@miftahcoding:~/Downloads$ ls
robi
miftah@miftahcoding:~/Downloads$ cd robi/
miftah@miftahcoding:~/Downloads/robi$ ls
miftah@miftahcoding:~/Downloads/robi$ pwd
/home/miftah/Downloads/robi
miftah@miftahcoding:~/Downloads/robi$ cd /
miftah@miftahcoding:/$ pwd
/
miftah@miftahcoding:/$ cd /home/miftah/Downloads/robi
miftah@miftahcoding:~/Downloads/robi$ ls
miftah@miftahcoding:~/Downloads/robi$ pwd
/home/miftah/Downloads/robi
miftah@miftahcoding:~/Downloads/robi$ cd ..
miftah@miftahcoding:~/Downloads$ ls
robi
miftah@miftahcoding:~/Downloads$ cd robi/
miftah@miftahcoding:~/Downloads/robi$ 
miftah@miftahcoding:~/Downloads/robi$ whoami
miftah
miftah@miftahcoding:~/Downloads/robi$ whoami
miftah
miftah@miftahcoding:~/Downloads/robi$ mkdir miftah/miftahcoding/neuralgem
mkdir: No such file or directory
miftah@miftahcoding:~/Downloads/robi$ mkdir -p miftah/miftahcoding/neuralgem
miftah@miftahcoding:~/Downloads/robi$ ls
miftah
miftah@miftahcoding:~/Downloads/robi$ cd miftah/
miftah@miftahcoding:~/Downloads/robi/miftah$ ls
miftahcoding
miftah@miftahcoding:~/Downloads/robi/miftah$ cd miftahcoding/
miftah@miftahcoding:~/Downloads/robi/miftah/miftahcoding$ ls
neuralgem
miftah@miftahcoding:~/Downloads/robi/miftah/miftahcoding$ cd neuralgem/
miftah@miftahcoding:~/Downloads/robi/miftah/miftahcoding/neuralgem$ ls
miftah@miftahcoding:~/Downloads/robi/miftah/miftahcoding/neuralgem$ cd ~
miftah@miftahcoding:~$ ls -lsah
total 72K
4.0K drwxr-x--- 15 miftah miftah 4.0K Jun  6 18:49 .
4.0K drwxr-xr-x  3 root   root   4.0K Jun  6 18:43 ..
4.0K -rw-r--r--  1 miftah miftah  220 Feb 13 18:16 .bash_logout
4.0K -rw-r--r--  1 miftah miftah 3.7K Feb 13 18:16 .bashrc
4.0K drwx------ 12 miftah miftah 4.0K Jun 12 21:38 .cache
4.0K drwx------ 14 miftah miftah 4.0K Jun 12 21:34 .config
4.0K drwx------  4 miftah miftah 4.0K Jun  6 18:49 .local
4.0K -rw-r--r--  1 miftah miftah  807 Feb 13 18:16 .profile
4.0K drwx------  2 miftah miftah 4.0K Jun  6 18:48 .ssh
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Desktop
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Documents
4.0K drwxr-xr-x  3 miftah miftah 4.0K Jun 12 21:58 Downloads
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Music
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Pictures
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Public
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Templates
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Videos
4.0K drwx------  5 miftah miftah 4.0K Jun  6 18:51 snap
miftah@miftahcoding:~$ ls -l -s -a -h
total 72K
4.0K drwxr-x--- 15 miftah miftah 4.0K Jun  6 18:49 .
4.0K drwxr-xr-x  3 root   root   4.0K Jun  6 18:43 ..
4.0K -rw-r--r--  1 miftah miftah  220 Feb 13 18:16 .bash_logout
4.0K -rw-r--r--  1 miftah miftah 3.7K Feb 13 18:16 .bashrc
4.0K drwx------ 12 miftah miftah 4.0K Jun 12 21:38 .cache
4.0K drwx------ 14 miftah miftah 4.0K Jun 12 21:34 .config
4.0K drwx------  4 miftah miftah 4.0K Jun  6 18:49 .local
4.0K -rw-r--r--  1 miftah miftah  807 Feb 13 18:16 .profile
4.0K drwx------  2 miftah miftah 4.0K Jun  6 18:48 .ssh
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Desktop
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Documents
4.0K drwxr-xr-x  3 miftah miftah 4.0K Jun 12 21:58 Downloads
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Music
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Pictures
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Public
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Templates
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Videos
4.0K drwx------  5 miftah miftah 4.0K Jun  6 18:51 snap
miftah@miftahcoding:~$ pwd
/home/miftah
miftah@miftahcoding:~$ ls
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos  snap
miftah@miftahcoding:~$ ls -lsah
total 72K
4.0K drwxr-x--- 15 miftah miftah 4.0K Jun  6 18:49 .
4.0K drwxr-xr-x  3 root   root   4.0K Jun  6 18:43 ..
4.0K -rw-r--r--  1 miftah miftah  220 Feb 13 18:16 .bash_logout
4.0K -rw-r--r--  1 miftah miftah 3.7K Feb 13 18:16 .bashrc
4.0K drwx------ 12 miftah miftah 4.0K Jun 12 21:38 .cache
4.0K drwx------ 14 miftah miftah 4.0K Jun 12 21:34 .config
4.0K drwx------  4 miftah miftah 4.0K Jun  6 18:49 .local
4.0K -rw-r--r--  1 miftah miftah  807 Feb 13 18:16 .profile
4.0K drwx------  2 miftah miftah 4.0K Jun  6 18:48 .ssh
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Desktop
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Documents
4.0K drwxr-xr-x  3 miftah miftah 4.0K Jun 12 21:58 Downloads
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Music
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Pictures
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Public
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Templates
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Videos
4.0K drwx------  5 miftah miftah 4.0K Jun  6 18:51 snap
miftah@miftahcoding:~$ mkdir 'Miftahul Islam'
miftah@miftahcoding:~$ ls
 Desktop   Documents   Downloads   'Miftahul Islam'   Music   Pictures   Public   Templates   Videos   snap
miftah@miftahcoding:~$ rmdir Miftahul\ Islam/
miftah@miftahcoding:~$ mkdir Miftahul\ Islam
miftah@miftahcoding:~$ ls
 Desktop   Documents   Downloads   'Miftahul Islam'   Music   Pictures   Public   Templates   Videos   snap
miftah@miftahcoding:~$ mkdir mifta\/h
mkdir: No such file or directory
miftah@miftahcoding:~$ mkdir  mifta/
miftah@miftahcoding:~$ mkdir "mifta/"
miftah@miftahcoding:~$ ls
 Desktop   Documents   Downloads   'Miftahul Islam'   Music   Pictures   Public   Templates   Videos   mifta   snap
miftah@miftahcoding:~$ 
miftah@miftahcoding:~$ "asdsad" > m.txt
asdsad: command not found
miftah@miftahcoding:~$ echo "habijabi" > m.txt
miftah@miftahcoding:~$ ls
 Desktop     Downloads          Music      Public      Videos   mifta
 Documents   'Miftahul Islam'   Pictures   Templates   m.txt    snap
miftah@miftahcoding:~$ echo "habijabi"
habijabi
miftah@miftahcoding:~$ echo "habijabi" > asdsa
miftah@miftahcoding:~$ ls
 Desktop     Downloads          Music      Public      Videos   m.txt   snap
 Documents   'Miftahul Islam'   Pictures   Templates   asdsa    mifta
miftah@miftahcoding:~$ cat asdsa 
habijabi
miftah@miftahcoding:~$ cat m.txt 
habijabi
miftah@miftahcoding:~$ ls > output.txt
miftah@miftahcoding:~$ cat output.txt 
Desktop
Documents
Downloads
Miftahul Islam
Music
Pictures
Public
Templates
Videos
asdsa
m.txt
mifta
output.txt
snap
miftah@miftahcoding:~$ ls
 Desktop     Downloads          Music      Public      Videos   m.txt   output.txt
 Documents   'Miftahul Islam'   Pictures   Templates   asdsa    mifta   snap
miftah@miftahcoding:~$ ls -lsah > o.txt
miftah@miftahcoding:~$ cat o.txt 
total 92K
4.0K drwxr-x--- 17 miftah miftah 4.0K Jun 12 22:17 .
4.0K drwxr-xr-x  3 root   root   4.0K Jun  6 18:43 ..
4.0K -rw-r--r--  1 miftah miftah  220 Feb 13 18:16 .bash_logout
4.0K -rw-r--r--  1 miftah miftah 3.7K Feb 13 18:16 .bashrc
4.0K drwx------ 12 miftah miftah 4.0K Jun 12 21:38 .cache
4.0K drwx------ 14 miftah miftah 4.0K Jun 12 21:34 .config
4.0K drwx------  4 miftah miftah 4.0K Jun  6 18:49 .local
4.0K -rw-r--r--  1 miftah miftah  807 Feb 13 18:16 .profile
4.0K drwx------  2 miftah miftah 4.0K Jun  6 18:48 .ssh
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Desktop
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Documents
4.0K drwxr-xr-x  3 miftah miftah 4.0K Jun 12 21:58 Downloads
4.0K drwxrwxr-x  2 miftah miftah 4.0K Jun 12 22:11 Miftahul Islam
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Music
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Pictures
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Public
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Templates
4.0K drwxr-xr-x  2 miftah miftah 4.0K Jun  6 18:49 Videos
4.0K -rw-rw-r--  1 miftah miftah    9 Jun 12 22:16 asdsa
4.0K -rw-rw-r--  1 miftah miftah    9 Jun 12 22:15 m.txt
4.0K drwxrwxr-x  2 miftah miftah 4.0K Jun 12 22:13 mifta
   0 -rw-rw-r--  1 miftah miftah    0 Jun 12 22:17 o.txt
4.0K -rw-rw-r--  1 miftah miftah  116 Jun 12 22:16 output.txt
4.0K drwx------  5 miftah miftah 4.0K Jun  6 18:51 snap
miftah@miftahcoding:~$ 
miftah@miftahcoding:~$ echo "ami miftahul islam"
ami miftahul islam
miftah@miftahcoding:~$ ls
 Desktop     Downloads          Music      Public      Videos   m.txt   o.txt        snap
 Documents   'Miftahul Islam'   Pictures   Templates   asdsa    mifta   output.txt
miftah@miftahcoding:~$ echo "ami miftahul islam" > m.txt 
miftah@miftahcoding:~$ cat m.txt 
ami miftahul islam
miftah@miftahcoding:~$ echo "ami miftahul islam" >> m.txt 
miftah@miftahcoding:~$ cat m.txt 
ami miftahul islam
ami miftahul islam
miftah@miftahcoding:~$ echo "append hobe" >> m.txt 
miftah@miftahcoding:~$ cat m.txt 
ami miftahul islam
ami miftahul islam
append hobe
miftah@miftahcoding:~$ echo "append hobe" > m.txt 
miftah@miftahcoding:~$ cat m.txt 
append hobe
miftah@miftahcoding:~$ 
```