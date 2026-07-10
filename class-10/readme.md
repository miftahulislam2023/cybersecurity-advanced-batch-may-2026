# Class 10

## Today's Topic
- bash history (**~/.bash_history**, **clear**, **CTRL + R**)
- redirection (**>** , **>>** , **<** , **<<** , **<<<**)
  -  `>` -> output redirection (overwriting)
     -  `ls -lsah > files.txt`
  -  `>>` -> output redirection (appending)
     -  `ls -lsah >> files.txt`
  -  `<` -> standard input redirection (from a file)
     -  **Syntax**: `command < filename`
     -  Use Cases: 
        - `sort < unsorted.txt` (Reads from file, sorts, outputs to terminal)
        - `mysql -u root -p db_name < backup.sql` (Load SQL commands)
  -  `<<` -> Here-Docoment Redirection (multi-line input)
     -  **Syntax**:
        ```bash
            command << DELIMITTER
            line 1
            line 2
            ...
            DELIMITTER
        ```
     - Use Cases:
       - Creating a multi-line file
         ```bash
         cat << EOF > test.txt
         Miftahul
         Islam
         Cyber Security
         EOF
         ```
       - Counting lines, words, and characters (Example: using `wc`)
         ```bash
            wc << goku
            line 1
            line 2
            ...
            goku
         ```
  -  `<<<` -> Here-String Redirection (single-line input)
     -  **Syntax**:
        ```bash
            command <<< "string"
        ```
     -  **Use Case**:
        -  Counting lines, words, and characters (Example: using `wc`)
           ```bash
           wc <<< "Miftahul Islam Cyber Security"
           ```
- streams (**stdin** (0), **stdout** (1), **stderr** (2), **> /dev/null**)
- bash configuration file (**/etc/skel**)
- aliases (**alias c, install**)
- seeing system usage (**top, htop, nload**)
- permissions (**d** -> directory, **-** -> file)
- `sudo adduser newuser`
- `passwd`
- `groups goku`
- `sudo usermod -aG sudo goku`

## Bash Commands
```bash
miftah@miftahcoding:~$ ls
cybersecurity-batch-2  file.txt  files  snap
miftah@miftahcoding:~$ ls > files
miftah@miftahcoding:~$ ls >> files
miftah@miftahcoding:~$ cat files
cybersecurity-batch-2
file.txt
files
snap
cybersecurity-batch-2
file.txt
files
snap
miftah@miftahcoding:~$ ls > files
miftah@miftahcoding:~$ cat files
cybersecurity-batch-2
file.txt
files
snap
miftah@miftahcoding:~$ wc -l files
4 files
miftah@miftahcoding:~$ wc -w files
4 files
miftah@miftahcoding:~$ wc -c files
42 files
miftah@miftahcoding:~$ wc -c < files
42
miftah@miftahcoding:~$ cat files
cybersecurity-batch-2
file.txt
files
snap
miftah@miftahcoding:~$ wc < asdsasa
bash: asdsasa: No such file or directory
miftah@miftahcoding:~$ wc (double greater than) EOF 
> asdasd
> adsaa
> asdsad
> asd
> sadasd
> asd
> aasdasd a dasdasd
> 
> sadasdasdas
> EOF
      9      10      66
miftah@miftahcoding:~$ wc (double greater than) goku
> adsada
> asdasdas asdasdsa
> asdasda asdasd asdasdas asdas das
> asd 
> asd
> asd
> asdasfs
> dfsdag
> sad
> g sg
>  dsfhdfgdfgjdfg hjfgh jg hf
> j fgh
> jfgh
> jhfg 
> jfgh
> fgh 
> jfgh 
>  fg
> hghj
> ghj
> goku
     20      30     170
miftah@miftahcoding:~$ 
miftah@miftahcoding:~$ cat files
cybersecurity-batch-2
file.txt
files
snap
miftah@miftahcoding:~$ cd /
miftah@miftahcoding:/$ ls
bin  boot  cdrom  dev  etc  home  lib  lost+found  media  mnt  opt  proc  root  run  sbin  snap  srv  swap.img  sys  tmp  usr  var
miftah@miftahcoding:/$ ls etc
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
miftah@miftahcoding:/$ ls root
ls: cannot open directory 'root': Permission denied
miftah@miftahcoding:/$ ls root >> test
bash: test: Permission denied
miftah@miftahcoding:/$ ls root >> /home/miftah/test
ls: cannot open directory 'root': Permission denied
miftah@miftahcoding:/$ ls root 2> /home/miftah/test
miftah@miftahcoding:/$ ls root 1> /home/miftah/test
ls: cannot open directory 'root': Permission denied
miftah@miftahcoding:/$ ls root 2>> /home/miftah/test
miftah@miftahcoding:/$ ls root 1>> /home/miftah/test
ls: cannot open directory 'root': Permission denied
miftah@miftahcoding:/$ ls root 2>> /home/miftah/test
miftah@miftahcoding:/$ ls etc 1> /home/miftah/test
miftah@miftahcoding:/$ ls etc 2> /home/miftah/test
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
miftah@miftahcoding:/$ ls etc 2> /home/miftah/stderr 1> /home/miftah/stdout
miftah@miftahcoding:/$ 
miftah@miftahcoding:/$ ls
bin  boot  cdrom  dev  etc  home  lib  lost+found  media  mnt  opt  proc  root  run  sbin  snap  srv  swap.img  sys  tmp  usr  var
miftah@miftahcoding:/$ cd ~
miftah@miftahcoding:~$ ls
cybersecurity-batch-2  file.txt  files  snap  test
miftah@miftahcoding:~$ cat test 
miftah@miftahcoding:~$ cat test 
ls: cannot open directory 'root': Permission denied
miftah@miftahcoding:~$ cat test 
miftah@miftahcoding:~$ cat test 
ls: cannot open directory 'root': Permission denied
ls: cannot open directory 'root': Permission denied
miftah@miftahcoding:~$ cat test 
ImageMagick-7
ModemManager
NetworkManager
PackageKit
UPower
X11
adduser.conf
alsa
alternatives
anacrontab
apm
apparmor
apparmor.d
apport
apt
avahi
bash.bashrc
bash_completion
bash_completion.d
bindresvport.blacklist
binfmt.d
bluetooth
brlapi.key
brltty
brltty.conf
ca-certificates
ca-certificates.conf
chatscripts
chrony
cloud
colord
console-setup
cracklib
credstore
credstore.encrypted
cron.d
cron.daily
cron.hourly
cron.monthly
cron.weekly
cron.yearly
crontab
cups
cupshelpers
dbus-1
dconf
debconf.conf
debian_version
debuginfod
default
deluser.conf
depmod.d
dhcp
dhcpcd.conf
dictionaries-common
dpkg
dracut.conf
dracut.conf.d
e2scrub.conf
emacs
environment
environment.d
ethertypes
flash-kernel
fonts
fprintd.conf
fstab
fuse.conf
fwupd
gai.conf
gdb
gdm3
geoclue
ghostscript
glvnd
gnome
gnome-remote-desktop
gnutls
gprofng.rc
groff
group
group-
grub.d
gshadow
gshadow-
gss
gtk-3.0
hdparm.conf
host.conf
hostname
hosts
hosts.allow
hosts.deny
hp
ifplugd
init
init.d
initramfs
initramfs-tools
inputrc
insserv.conf.d
ipp-usb
issue
issue.net
kdump
kernel
krb5.conf.d
ld.so.cache
ld.so.conf
ld.so.conf.d
ldap
legal
libao.conf
libaudit.conf
libblockdev
libibverbs.d
libnl-3
locale.conf
locale.gen
localtime
logcheck
login.defs
logrotate.conf
logrotate.d
lsb-release
machine-id
magic
magic.mime
manpath.config
mime.types
mke2fs.conf
modprobe.d
modules
modules-load.d
mtab
nanorc
netconfig
netplan
network
networkd-dispatcher
networks
newt
nftables.conf
nsswitch.conf
openal
openni2
openvpn
opt
os-release
pam.conf
pam.d
paperspecs
passwd
passwd-
pcmcia
perl
pki
plymouth
pm
pnm2ppa.conf
polkit-1
ppp
profile
profile.d
protocols
pulse
python3
python3.14
rc0.d
rc1.d
rc2.d
rc3.d
rc4.d
rc5.d
rc6.d
rcS.d
resolv.conf
rmt
rpc
rsyslog.conf
rsyslog.d
rygel.conf
sane.d
screenrc
security
selinux
sensors.d
sensors3.conf
services
sgml
shadow
shadow-
shells
skel
snmp
speech-dispatcher
ssh
ssl
sssd
subgid
subgid-
subuid
subuid-
sudo.conf
sudo_logsrvd.conf
sudoers
sudoers.d
supercat
sysctl.d
sysstat
systemd
terminfo
timezone
timidity
tmpfiles.d
tpm2-tss
ubuntu-advantage
ucf.conf
udev
udisks2
ufw
update-manager
update-motd.d
update-notifier
usb_modeswitch.conf
usb_modeswitch.d
vconsole.conf
vdpau_wrapper.cfg
vim
vtrgb
vulkan
wgetrc
whoopsie
wpa_supplicant
xattr.conf
xdg
xemacs21
xml
zsh_command_not_found
miftah@miftahcoding:~$ cat test 
miftah@miftahcoding:~$ ls
cybersecurity-batch-2  file.txt  files  snap  stderr  stdout  test
miftah@miftahcoding:~$ cat stderr 
miftah@miftahcoding:~$ cat stdout
ImageMagick-7
ModemManager
NetworkManager
PackageKit
UPower
X11
adduser.conf
alsa
alternatives
anacrontab
apm
apparmor
apparmor.d
apport
apt
avahi
bash.bashrc
bash_completion
bash_completion.d
bindresvport.blacklist
binfmt.d
bluetooth
brlapi.key
brltty
brltty.conf
ca-certificates
ca-certificates.conf
chatscripts
chrony
cloud
colord
console-setup
cracklib
credstore
credstore.encrypted
cron.d
cron.daily
cron.hourly
cron.monthly
cron.weekly
cron.yearly
crontab
cups
cupshelpers
dbus-1
dconf
debconf.conf
debian_version
debuginfod
default
deluser.conf
depmod.d
dhcp
dhcpcd.conf
dictionaries-common
dpkg
dracut.conf
dracut.conf.d
e2scrub.conf
emacs
environment
environment.d
ethertypes
flash-kernel
fonts
fprintd.conf
fstab
fuse.conf
fwupd
gai.conf
gdb
gdm3
geoclue
ghostscript
glvnd
gnome
gnome-remote-desktop
gnutls
gprofng.rc
groff
group
group-
grub.d
gshadow
gshadow-
gss
gtk-3.0
hdparm.conf
host.conf
hostname
hosts
hosts.allow
hosts.deny
hp
ifplugd
init
init.d
initramfs
initramfs-tools
inputrc
insserv.conf.d
ipp-usb
issue
issue.net
kdump
kernel
krb5.conf.d
ld.so.cache
ld.so.conf
ld.so.conf.d
ldap
legal
libao.conf
libaudit.conf
libblockdev
libibverbs.d
libnl-3
locale.conf
locale.gen
localtime
logcheck
login.defs
logrotate.conf
logrotate.d
lsb-release
machine-id
magic
magic.mime
manpath.config
mime.types
mke2fs.conf
modprobe.d
modules
modules-load.d
mtab
nanorc
netconfig
netplan
network
networkd-dispatcher
networks
newt
nftables.conf
nsswitch.conf
openal
openni2
openvpn
opt
os-release
pam.conf
pam.d
paperspecs
passwd
passwd-
pcmcia
perl
pki
plymouth
pm
pnm2ppa.conf
polkit-1
ppp
profile
profile.d
protocols
pulse
python3
python3.14
rc0.d
rc1.d
rc2.d
rc3.d
rc4.d
rc5.d
rc6.d
rcS.d
resolv.conf
rmt
rpc
rsyslog.conf
rsyslog.d
rygel.conf
sane.d
screenrc
security
selinux
sensors.d
sensors3.conf
services
sgml
shadow
shadow-
shells
skel
snmp
speech-dispatcher
ssh
ssl
sssd
subgid
subgid-
subuid
subuid-
sudo.conf
sudo_logsrvd.conf
sudoers
sudoers.d
supercat
sysctl.d
sysstat
systemd
terminfo
timezone
timidity
tmpfiles.d
tpm2-tss
ubuntu-advantage
ucf.conf
udev
udisks2
ufw
update-manager
update-motd.d
update-notifier
usb_modeswitch.conf
usb_modeswitch.d
vconsole.conf
vdpau_wrapper.cfg
vim
vtrgb
vulkan
wgetrc
whoopsie
wpa_supplicant
xattr.conf
xdg
xemacs21
xml
zsh_command_not_found
miftah@miftahcoding:~$ ls
cybersecurity-batch-2  file.txt  files  snap  stderr  stdout  test
miftah@miftahcoding:~$ ls > /dev/null
miftah@miftahcoding:~$ 
miftah@miftahcoding:/$ cd ~
miftah@miftahcoding:~$ ls -lsah
total 64K
4.0K drwxr-x---  9 miftah miftah 4.0K Jul 10 22:17 .
4.0K drwxr-xr-x  3 root   root   4.0K Jun  6 18:43 ..
4.0K -rw-------  1 miftah miftah 3.5K Jul 10 22:21 .bash_history
4.0K -rw-r--r--  1 miftah miftah  220 Feb 13 18:16 .bash_logout
4.0K -rw-r--r--  1 miftah miftah 3.7K Feb 13 18:16 .bashrc
4.0K drwx------ 13 miftah miftah 4.0K Jul  3 22:03 .cache
4.0K drwx------ 17 miftah miftah 4.0K Jul  3 22:33 .config
4.0K drwx------  2 miftah miftah 4.0K Jul  3 22:03 .gnupg
4.0K drwx------  4 miftah miftah 4.0K Jun  6 18:49 .local
4.0K -rw-r--r--  1 miftah miftah  807 Feb 13 18:16 .profile
4.0K drwx------  2 miftah miftah 4.0K Jun  6 18:48 .ssh
4.0K drwxrwxr-x  2 miftah miftah 4.0K Jun 19 22:29 cybersecurity-batch-2
4.0K -rw-rw-r--  1 miftah miftah  224 Jul  3 22:16 file.txt
4.0K -rw-rw-r--  1 miftah miftah   42 Jul 10 21:51 files
4.0K drwx------  5 miftah miftah 4.0K Jun  6 18:51 snap
   0 -rw-rw-r--  1 miftah miftah    0 Jul 10 22:17 stderr
4.0K -rw-rw-r--  1 miftah miftah 2.3K Jul 10 22:17 stdout
   0 -rw-rw-r--  1 miftah miftah    0 Jul 10 22:16 test
miftah@miftahcoding:~$ less .bash
.bash_history  .bash_logout   .bashrc        
miftah@miftahcoding:~$ less .bash
.bash_history  .bash_logout   .bashrc        
miftah@miftahcoding:~$ less .bash
.bash_history  .bash_logout   .bashrc        
miftah@miftahcoding:~$ less .bashrc 
miftah@miftahcoding:~$ nano .bashrc
miftah@miftahcoding:~$ less .bashrc 
miftah@miftahcoding:~$ cd /etc/skel
miftah@miftahcoding:/etc/skel$ ls
miftah@miftahcoding:/etc/skel$ ls -lash
total 28K
4.0K drwxr-xr-x   2 root root 4.0K Apr 23 07:18 .
 12K drwxr-xr-x 146 root root  12K Jun  6 18:49 ..
4.0K -rw-r--r--   1 root root  220 Feb 13 18:16 .bash_logout
4.0K -rw-r--r--   1 root root 3.7K Feb 13 18:16 .bashrc
4.0K -rw-r--r--   1 root root  807 Feb 13 18:16 .profile
miftah@miftahcoding:/etc/skel$ cd ~
miftah@miftahcoding:~$ ls
cybersecurity-batch-2  file.txt  files  snap  stderr  stdout  test
miftah@miftahcoding:~$ 
miftah@miftahcoding:~$ i htop
[sudo: authenticate] Password:     
htop is already the newest version (3.4.1-5build2).
Summary:                    
  Upgrading: 0, Installing: 0, Removing: 0, Not Upgrading: 15
miftah@miftahcoding:~$ nload
Command 'nload' not found, but can be installed with:
sudo apt install nload
miftah@miftahcoding:~$ i nload
Installing:                     
  nload

Summary:
  Upgrading: 0, Installing: 1, Removing: 0, Not Upgrading: 15
  Download size: 48.9 kB
  Space needed: 151 kB / 8,641 MB available

Get:1 http://bd.archive.ubuntu.com/ubuntu resolute/universe arm64 nload arm64 0.7.4-2build4 [48.9 kB]
Fetched 48.9 kB in 1s (46.7 kB/s)
Selecting previously unselected package nload.
(Reading database… 159569 files and directories currently installed.)
Preparing to unpack …/nload_0.7.4-2build4_arm64.deb…
Unpacking nload (0.7.4-2build4)…
Setting up nload (0.7.4-2build4)…
Processing triggers for man-db (2.13.1-1build1)…
miftah@miftahcoding:~$ r nload
REMOVING:                       
  nload

Summary:
  Upgrading: 0, Installing: 0, Removing: 1, Not Upgrading: 15
  Freed space: 151 kB

Continue? [Y/n] y
(Reading database… 159572 files and directories currently installed.)
Removing nload (0.7.4-2build4)…
Processing triggers for man-db (2.13.1-1build1)…
```