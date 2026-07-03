# Class - 9

## Today's Commands
- wc -l (line count)
- nano (text editor)
- |
- man
- uniq (it only works on adjacent matching lines.)
- sort
- su (‘superuser’ or ‘switch user’)

## Piping
- The Unix command line provides a shortcut that avoids you having to create a temporary file, by **taking the output from one command** (referred to as standard output or **STDOUT**) and **feeding it directly in as the input to another command** (standard input or **STDIN**). It’s as though you’ve connected a **pipe** between one command’s output and the next command’s input, so much so that this process is actually referred to as piping the data from one command to another.
- **Spaces** around the pipe character **aren’t important**

## Manuals
- **Most** command line tools come with a brief (and sometimes not-so-brief) instruction manual, accessed through the **man** (manual) command. The output is **automatically piped through** your pager, which will typically be **less**, so you can move back and forth through the output, then press q when you’re finished

## Root User
- root can modify or delete any file in any directory on the system, regardless of who owns them; root can rewrite firewall rules or start network services that could potentially open the machine up to an attack; root can shut down the machine even if other people are still using it. In short, root can do just about anything
- **su** (‘superuser’ or ‘switch user’) allows you to change to another user on the machine without having to log out and in again. When used with no arguments, it assumes you want to change to the root user (hence the first interpretation of the name), but you can pass a username to it in order to switch to a specific user account (the second interpretation). 
- **sudo** (as in “switch user and do this command”) is used to prefix a command that has to be run with superuser privileges. A configuration file is used to define which users can use sudo, and which commands they can run. When running a command like this, the user is prompted for their own password, which is then cached for a period of time (defaulting to 15 minutes), so if they need to run multiple superuser-level commands they don’t keep getting continually asked to type it in.

## Bash commands
```bash
miftah@miftahcoding:~$ ls
cybersecurity-batch-2  habijabi  snap  t2  t3
miftah@miftahcoding:~$ less habijabi 
miftah@miftahcoding:~$ less t2
miftah@miftahcoding:~$ less t3
miftah@miftahcoding:~$ echo >> "I have two friends."
miftah@miftahcoding:~$ ls
'I have two friends.'   cybersecurity-batch-2   habijabi   snap   t2   t3
miftah@miftahcoding:~$ cat I\ have\ two\ friends. 

miftah@miftahcoding:~$ rm I habijabi 
rm: cannot remove 'I': No such file or directory
miftah@miftahcoding:~$ rm I\ have\ two\ friends. 
miftah@miftahcoding:~$ ls
cybersecurity-batch-2  snap  t2  t3
miftah@miftahcoding:~$ echo "I have two friends." >> file.txt
miftah@miftahcoding:~$ ls
cybersecurity-batch-2  file.txt  snap  t2  t3
miftah@miftahcoding:~$ cat file.txt 
I have two friends.
miftah@miftahcoding:~$ echo "I have two friends." >> file.txt
miftah@miftahcoding:~$ echo "I have two friends." >> file.txt
miftah@miftahcoding:~$ echo "I have two friends." >> file.txt
miftah@miftahcoding:~$ echo "I have two friends." >> file.txt
miftah@miftahcoding:~$ echo "I have two friends." >> file.txt
miftah@miftahcoding:~$ echo "I have two friends." >> file.txt
miftah@miftahcoding:~$ cat file.txt 
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
miftah@miftahcoding:~$ wc file.txt 
  7  28 140 file.txt
miftah@miftahcoding:~$ nano file2.txt
miftah@miftahcoding:~$ wc file2.txt 
 1  1 11 file2.txt
miftah@miftahcoding:~$ cat file
file2.txt  file.txt   
miftah@miftahcoding:~$ cat file
file2.txt  file.txt   
miftah@miftahcoding:~$ cat file2.txt 
Bangladesh
miftah@miftahcoding:~$ 
miftah@miftahcoding:~$ cat file2.txt 
Bangladesh
miftah@miftahcoding:~$ wc file2.txt 
 1  1 11 file2.txt
miftah@miftahcoding:~$ man cat
miftah@miftahcoding:~$ man cd
No manual entry for cd
miftah@miftahcoding:~$ man mkdir
miftah@miftahcoding:~$ man man
miftah@miftahcoding:~$ cat -A file2.txt 
Bangladesh$
miftah@miftahcoding:~$ ls
cybersecurity-batch-2  file.txt  file2.txt  snap  t2  t3
miftah@miftahcoding:~$ ls >> files
miftah@miftahcoding:~$ ls
cybersecurity-batch-2  file.txt  file2.txt  files  snap  t2  t3
miftah@miftahcoding:~$ cat files
cybersecurity-batch-2
file.txt
file2.txt
files
snap
t2
t3
miftah@miftahcoding:~$ cat -A files
cybersecurity-batch-2$
file.txt$
file2.txt$
files$
snap$
t2$
t3$
miftah@miftahcoding:~$ ls | wc
      7       7      58
miftah@miftahcoding:~$ ls | wc -l
7
miftah@miftahcoding:~$ ls | wc -c
58
miftah@miftahcoding:~$ ls | wc -w
7
miftah@miftahcoding:~$ 
miftah@miftahcoding:~$ uniq file.txt
I have two friends.
miftah@miftahcoding:~$ cat file.txt 
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
miftah@miftahcoding:~$ echo "I have two friends." >> file.txt
miftah@miftahcoding:~$ echo "I have three friends." >> file.txt
miftah@miftahcoding:~$ cat file.txt 
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have three friends.
miftah@miftahcoding:~$ echo "I have two friends." >> file.txt
miftah@miftahcoding:~$ cat file.txt 
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have three friends.
I have two friends.
miftah@miftahcoding:~$ echo "I have three friends." >> file.txt
miftah@miftahcoding:~$ cat file.txt 
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have three friends.
I have two friends.
I have three friends.
miftah@miftahcoding:~$ 
miftah@miftahcoding:~$ rm file-2.txt
rm: cannot remove 'file-2.txt': No such file or directory
miftah@miftahcoding:~$ ls
cybersecurity-batch-2  file.txt  file2.txt  files  snap  t2  t3
miftah@miftahcoding:~$ rm file2.txt files t2 t3 
miftah@miftahcoding:~$ ls
cybersecurity-batch-2  file.txt  snap
miftah@miftahcoding:~$ cat file.txt 
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have three friends.
I have two friends.
I have three friends.
miftah@miftahcoding:~$ cat file.txt | wc
     11      44     224
miftah@miftahcoding:~$ cat file.txt | uniq 
I have two friends.
I have three friends.
I have two friends.
I have three friends.
miftah@miftahcoding:~$ sort file.txt | cat 
I have three friends.
I have three friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
I have two friends.
miftah@miftahcoding:~$ sort file.txt | uniq
I have three friends.
I have two friends.
miftah@miftahcoding:~$ sort file.txt | uniq | wc -l
2
miftah@miftahcoding:~$ 
miftah@miftahcoding:~$ whoami 
miftah
miftah@miftahcoding:~$ cd /
miftah@miftahcoding:/$ ls
bin  boot  cdrom  dev  etc  home  lib  lost+found  media  mnt  opt  proc  root  run  sbin  snap  srv  swap.img  sys  tmp  usr  var
miftah@miftahcoding:/$ cd root/
bash: cd: root/: Permission denied
miftah@miftahcoding:/$ cd run/
miftah@miftahcoding:/run$ cd ..
miftah@miftahcoding:/$ ls -lsah
total 3.1G
4.0K drwxr-xr-x  20 root root 4.0K Jun  6 18:42 .
4.0K drwxr-xr-x  20 root root 4.0K Jun  6 18:42 ..
   0 lrwxrwxrwx   1 root root    7 Apr 20 14:46 bin -> usr/bin
4.0K drwxr-xr-x   4 root root 4.0K Jun 12 21:34 boot
4.0K dr-xr-xr-x   2 root root 4.0K Apr 23 07:56 cdrom
   0 drwxr-xr-x  19 root root 4.1K Jul  3 21:52 dev
 12K drwxr-xr-x 146 root root  12K Jun  6 18:49 etc
4.0K drwxr-xr-x   3 root root 4.0K Jun  6 18:43 home
   0 lrwxrwxrwx   1 root root    7 Apr 20 14:46 lib -> usr/lib
 16K drwx------   2 root root  16K Jun  6 18:36 lost+found
4.0K drwxr-xr-x   2 root root 4.0K Apr 23 07:17 media
4.0K drwxr-xr-x   2 root root 4.0K Apr 23 07:17 mnt
4.0K drwxr-xr-x   2 root root 4.0K Apr 23 07:17 opt
   0 dr-xr-xr-x 275 root root    0 Jul  3 21:52 proc
4.0K drwx------   5 root root 4.0K Jun  6 18:48 root
   0 drwxr-xr-x  43 root root 1000 Jul  3 21:52 run
   0 lrwxrwxrwx   1 root root    8 Apr 20 14:46 sbin -> usr/sbin
4.0K drwxr-xr-x  14 root root 4.0K Apr 23 07:30 snap
4.0K drwxr-xr-x   2 root root 4.0K Apr 23 07:17 srv
3.1G -rw-------   1 root root 3.1G Jun  6 18:42 swap.img
   0 dr-xr-xr-x  13 root root    0 Jul  3 21:52 sys
   0 drwxrwxrwt  16 root root  360 Jul  3 22:07 tmp
4.0K drwxr-xr-x  11 root root 4.0K Apr 23 07:17 usr
4.0K drwxr-xr-x  14 root root 4.0K Jun  6 18:48 var
miftah@miftahcoding:/$ su
Password: 

su: Authentication failure
miftah@miftahcoding:/$ 
miftah@miftahcoding:/$ su
Password: 
su: Authentication failure
miftah@miftahcoding:/$ sudo su
[sudo: authenticate] Password:     
root@miftahcoding:/# ls
bin  boot  cdrom  dev  etc  home  lib  lost+found  media  mnt  opt  proc  root  run  sbin  snap  srv  swap.img  sys  tmp  usr  var
root@miftahcoding:/# cd root/
root@miftahcoding:~# ls
snap
root@miftahcoding:~# cd snap/
root@miftahcoding:~/snap# ls
desktop-security-center  firefox  mesa-2404  prompting-client  snap-store  snapd-desktop-integration
root@miftahcoding:~/snap# su miftah
miftah@miftahcoding:/root/snap$ su root
Password: 
su: Authentication failure
miftah@miftahcoding:/root/snap$ cd etc
bash: cd: etc: Permission denied
miftah@miftahcoding:/root/snap$ ls
ls: cannot open file '.': Permission denied
miftah@miftahcoding:/root/snap$ cd /
miftah@miftahcoding:/$ cd etc
miftah@miftahcoding:/etc$ ls
ImageMagick-7           colord               environment           hosts            logcheck             pam.d         rsyslog.d          systemd
ModemManager            console-setup        environment.d         hosts.allow      login.defs           paperspecs    rygel.conf         terminfo
NetworkManager          cracklib             ethertypes            hosts.deny       logrotate.conf       passwd        sane.d             timezone
PackageKit              credstore            flash-kernel          hp               logrotate.d          passwd-       screenrc           timidity
UPower                  credstore.encrypted  fonts                 ifplugd          lsb-release          pcmcia        security           tmpfiles.d
X11                     cron.d               fprintd.conf          init             machine-id           perl          selinux            tpm2-tss
adduser.conf            cron.daily           fstab                 init.d           magic                pki           sensors.d          ubuntu-advantage
alsa                    cron.hourly          fuse.conf             initramfs        magic.mime           plymouth      sensors3.conf      ucf.conf
alternatives            cron.monthly         fwupd                 initramfs-tools  manpath.config       pm            services           udev
anacrontab              cron.weekly          gai.conf              inputrc          mime.types           pnm2ppa.conf  sgml               udisks2
apm                     cron.yearly          gdb                   insserv.conf.d   mke2fs.conf          polkit-1      shadow             ufw
apparmor                crontab              gdm3                  ipp-usb          modprobe.d           ppp           shadow-            update-manager
apparmor.d              cups                 geoclue               issue            modules              profile       shells             update-motd.d
apport                  cupshelpers          ghostscript           issue.net        modules-load.d       profile.d     skel               update-notifier
apt                     dbus-1               glvnd                 kdump            mtab                 protocols     snmp               usb_modeswitch.conf
avahi                   dconf                gnome                 kernel           nanorc               pulse         speech-dispatcher  usb_modeswitch.d
bash.bashrc             debconf.conf         gnome-remote-desktop  krb5.conf.d      netconfig            python3       ssh                vconsole.conf
bash_completion         debian_version       gnutls                ld.so.cache      netplan              python3.14    ssl                vdpau_wrapper.cfg
bash_completion.d       debuginfod           gprofng.rc            ld.so.conf       network              rc0.d         sssd               vim
bindresvport.blacklist  default              groff                 ld.so.conf.d     networkd-dispatcher  rc1.d         subgid             vtrgb
binfmt.d                deluser.conf         group                 ldap             networks             rc2.d         subgid-            vulkan
bluetooth               depmod.d             group-                legal            newt                 rc3.d         subuid             wgetrc
brlapi.key              dhcp                 grub.d                libao.conf       nftables.conf        rc4.d         subuid-            whoopsie
brltty                  dhcpcd.conf          gshadow               libaudit.conf    nsswitch.conf        rc5.d         sudo.conf          wpa_supplicant
brltty.conf             dictionaries-common  gshadow-              libblockdev      openal               rc6.d         sudo_logsrvd.conf  xattr.conf
ca-certificates         dpkg                 gss                   libibverbs.d     openni2              rcS.d         sudoers            xdg
ca-certificates.conf    dracut.conf          gtk-3.0               libnl-3          openvpn              resolv.conf   sudoers.d          xemacs21
chatscripts             dracut.conf.d        hdparm.conf           locale.conf      opt                  rmt           supercat           xml
chrony                  e2scrub.conf         host.conf             locale.gen       os-release           rpc           sysctl.d           zsh_command_not_found
cloud                   emacs                hostname              localtime        pam.conf             rsyslog.conf  sysstat
miftah@miftahcoding:/etc$ ls -slah | less
miftah@miftahcoding:/etc$ cd shadow
bash: cd: shadow: Not a directory
miftah@miftahcoding:/etc$ 
miftah@miftahcoding:~$ sudo apt install htop
[sudo: authenticate] Password:     
Installing:                     
  htop

Suggested packages:
  lm-sensors

Summary:
  Upgrading: 0, Installing: 1, Removing: 0, Not Upgrading: 15
  Download size: 175 kB
  Space needed: 455 kB / 8,640 MB available

Get:1 http://bd.archive.ubuntu.com/ubuntu resolute/main arm64 htop arm64 3.4.1-5build2 [175 kB]
Fetched 175 kB in 2s (70.1 kB/s)
Selecting previously unselected package htop.
(Reading database… 159552 files and directories currently installed.)
Preparing to unpack …/htop_3.4.1-5build2_arm64.deb…
Unpacking htop (3.4.1-5build2)…
Setting up htop (3.4.1-5build2)…
Processing triggers for desktop-file-utils (0.28-1build1)…
Processing triggers for hicolor-icon-theme (0.18-2build1)…
Processing triggers for gnome-menus (3.38.1-1ubuntu1)…
Processing triggers for man-db (2.13.1-1build1)…
miftah@miftahcoding:~$ htop
miftah@miftahcoding:~$ sudo apt install tree
Installing:                     
  tree

Summary:
  Upgrading: 0, Installing: 1, Removing: 0, Not Upgrading: 15
  Download size: 52.7 kB
  Space needed: 162 kB / 8,639 MB available

Get:1 http://bd.archive.ubuntu.com/ubuntu resolute/universe arm64 tree arm64 2.3.1-1 [52.7 kB]
Fetched 52.7 kB in 1s (39.1 kB/s)
Selecting previously unselected package tree.
(Reading database… 159562 files and directories currently installed.)
Preparing to unpack …/tree_2.3.1-1_arm64.deb…
Unpacking tree (2.3.1-1)…
Setting up tree (2.3.1-1)…
Processing triggers for man-db (2.13.1-1build1)…
miftah@miftahcoding:~$ tree
.
├── cybersecurity-batch-2
│   ├── m
│   └── m2.txt
├── file.txt
└── snap
    ├── firefox
    │   ├── 8105
    │   ├── common
    │   └── current -> 8105
    ├── prompting-client
    │   ├── 203
    │   │   ├── Desktop
    │   │   ├── Documents
    │   │   ├── Downloads
    │   │   ├── Music
    │   │   ├── Pictures
    │   │   ├── Public
    │   │   ├── Templates
    │   │   └── Videos
    │   ├── 221
    │   │   ├── Desktop
    │   │   ├── Documents
    │   │   ├── Downloads
    │   │   ├── Music
    │   │   ├── Pictures
    │   │   ├── Public
    │   │   ├── Templates
    │   │   └── Videos
    │   ├── common
    │   └── current -> 221
    └── snapd-desktop-integration
        ├── 363
        │   ├── Desktop
        │   ├── Documents
        │   ├── Downloads
        │   ├── Music
        │   ├── Pictures
        │   ├── Public
        │   ├── Templates
        │   └── Videos
        ├── common
        └── current -> 363

40 directories, 3 files
miftah@miftahcoding:~$ 
```