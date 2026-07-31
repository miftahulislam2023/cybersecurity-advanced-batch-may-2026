# Class 11

## Today's Topic
- Working with Commands (type, which, man, whatis, alias)
  - which -> show path of a command
  - type -> show type of a command
  - man -> show manual of a command
  - whatis -> show one-line description of a command
  - alias -> create an alias for a command
- System Usages
  - top
  - htop
  - btop
  - uptime
  - df -h -i
  - free -m
  - nload
- Installing Softwares
  - sudo apt install apache
  - apt
    - search -> package search in repositories
    - install -> install a package
    - remove -> remove a package
    - autoremove -> remove unnecessary packages
    - dist-upgrade -> upgrade the system
    - show [package-name] -> show information about a package
- Text Editing Basic
  - nano
  - vim
  - mousepad
- find
  - -name -> search by name
  - -type (d, f, l) -> search by type (directory, file, link)
  - -iname -> search by name (case-insensitive)
  - -size -> search by size
  - -mtime -> search by modification time
  - -user -> search by user
  - -group -> search by group

## Bash Shortcuts
### Navigation Shortcuts
- Ctrl + A : Move to the beginning of the line
- Ctrl + E : Move to the end of the line
- Ctrl + B : Move back one character
- Ctrl + F : Move forward one character
- Alt + B : Move back one word
- Alt + F : Move forward one word
### Editing Shortcuts
- Ctrl + U : Cut/delete text from the cursor to the beginning of the line
- Ctrl + K : Cut/delete text from the cursor to the end of the line
- Ctrl + W : Cut/delete the word before the cursor
- Ctrl + Y : Paste the last cut text
- Ctrl + L : Clear the terminal screen
- Ctrl + C : Terminate the currently running command
### History Shortcuts
- Ctrl + R : Search command history (reverse search)
- Ctrl + G : Exit history search mode
- Ctrl + P : Go to the previous command in history
- Ctrl + N : Go to the next command in history

## পাইপলাইন এবং টেক্সট প্রসেসিং (Pipelines & Text Processing)

### পাইপলাইন (`|`) এর মেকানিজম

* **ব্যাখ্যা:** লিনাক্সের ফিলোসফি হলো—"এমন ছোট ছোট টুল বানাও যা কেবল একটি কাজই নিখুঁতভাবে করবে"। পাইপলাইন এই ছোট টুলগুলোকে একসাথে জুড়ে দিয়ে চেইন তৈরি করে। বামপাশের কমান্ডের `Stdout` (Standard Output) ডানপাশের কমান্ডের `Stdin` (Standard Input) হিসেবে কাজ করে।

### কোর ইউটিলিটিজ ও অপশনস

* `cat` (Concatenate): ফাইলের ভেতরের লেখা রিড করে আউটপুটে পাঠায়।
* *অপশন `-n`:* প্রতিটি লাইনের শুরুতে লাইন নাম্বার বসায়।


* `sort`: টেক্সট লাইনের বিন্যাস ঠিক করে।
* *অপশন `-n`:* আলফাবেটিক্যালের বদলে নিউমেরিক্যালি (১, ২, ১০) সর্ট করে।
* *অপশন `-r`:* উল্টো করে (Z to A বা বড় থেকে ছোট) সাজায়।


* `uniq`: ডুপ্লিকেট লাইন রিমুভ করে। এটি কাজ করার শর্ত হলো ইনপুট ফাইলটি অবশ্যই সর্টেড হতে হবে।
* *অপশন `-c`:* কোন লাইনটি কতবার রিপিট হয়েছে তার সংখ্যা দেখায়।
* *অপশন `-d`:* শুধু ডুপ্লিকেট লাইনগুলো ফিল্টার করে দেখায়।


* `head` & `tail`:
* `head -n 5`: ফাইলের প্রথম ৫টি লাইন দেখায়।
* `tail -n 5`: ফাইলের শেষ ৫টি লাইন দেখায়।


* `tee`: পাইপলাইনের মাঝখানে বসে ডেটাকে দ্বিমুখী করে। স্ক্রিনেও আউটপুট পাঠায়, আবার ফাইলে লিখেও রাখে।
* *অপশন `-a`:* ফাইল ওভাররাইট না করে নিচে নতুন ডেটা অ্যাপেন্ড (Append) করে।



### `grep` (Global Regular Expression Print)

* **গভীর ব্যাখ্যা:** এটি একটি টেক্সট সার্চ ইঞ্জিন। হাজার লাইনের ফাইল থেকে সেকেন্ডের মধ্যে নির্দিষ্ট প্যাটার্ন ফিল্টার করে দেয়।
* **কমান্ড ব্যবচ্ছেদ (`grep -v -n -c -r "pattern" .`):**
* `-v` (Invert Match): উল্টো কাজ করে। যা সার্চ করছেন তা বাদে বাকি সব লাইন প্রিন্ট করবে।
* `-n` (Line Number): ফাইলটির কত নম্বর লাইনে ওই ম্যাচটি পাওয়া গেছে তা বামে দেখাবে।
* `-c` (Count): লাইনের ভেতরের কনটেন্ট না দেখিয়ে শুধু ম্যাচ পাওয়া লাইনের মোট সংখ্যা দেখাবে।
* `-r` (Recursive): বর্তমান ফোল্ডারের ভেতরে যত সাব-ফোল্ডার ও ফাইল আছে সবগুলোর ভেতরে সার্চ চালাবে।
* `.`: সার্চের স্টার্টিং পয়েন্ট বর্তমান ডিরেক্টরি।


* **বাস্তবসম্মত উদাহরণ ও ইউজ কেস (পাইপলাইন চেইন):**
* *ইউজ কেস ১ (লগ ফাইল থেকে ইউনিক আইপি বের করা):* অ্যাক্সেস লগ থেকে কারা রিকোয়েস্ট পাঠাচ্ছে তাদের আইপি বের করে, সর্ট করে, ইউনিক আইপিগুলোর কাউন্ট দেখা।
```bash
cat access.log | cut -d' ' -f1 | sort | uniq -c | sort -nr

```


* *ইউজ কেস ২ (প্রোজেক্টের সব ফাইলে নির্দিষ্ট কোড খোঁজা):* নোড মডিউল বাদে আপনার কোডের কোথায় "auth" ফাংশন আছে লাইন নম্বরসহ বের করা।
```bash
grep -rn "auth" --exclude-dir=node_modules .

```





### `tail -f -n` (লাইভ মনিটরিং)

* **ইউজ কেস:** প্রোডাকশন সার্ভারে যখন কোনো ইউজার বলে "লগইন হচ্ছে না", তখন লাইভ ট্রাফিক ট্র্যাকিং করা।
```bash
    tail -f -n 50 /var/log/nginx/error.log

```


*(এটি শেষ ৫০টি এরর লাইন দেখাবে এবং টার্মিনাল হোল্ড করে রাখবে। নতুন কোনো এরর আসার সাথে সাথে স্ক্রিনে রিয়েল-টাইমে প্রিন্ট হবে)*।

---

## কমান্ড ইন্সপেকশন ও শর্টকাটস (Working with Commands)

* `type`: শেল কীভাবে একটি কমান্ডকে চেনে তা নির্ধারণ করে। লিনাক্সে কমান্ড ৪ রকম হতে পারে: alias, keyword, function, builtin, অথবা এক্সটার্নাল ফাইল।
* *উদাহরণ:* `type ll` -> `ll is aliased to ls -l`


* `which`: আপনার এনভায়রনমেন্ট পাথে (`$PATH`) থাকা এক্সিকিউটেবল ফাইলের অ্যাবসোলিউট পাথ দেখায়।
* *ইউজ কেস:* সিস্টেমে নোডের কোন ভার্সন বা কোন বাইনারি রান হচ্ছে তা নিশ্চিত করা: `which node` -> `/usr/.nvm/versions/node/v20.0.0/bin/node`.


* `man`: লিনাক্সের অফলাইন এনসাইক্লোপিডিয়া। প্রতিটি কমান্ডের অপশন ও ফ্ল্যাগের অফিশিয়াল ডকুমেন্টেশন।
```bash
man tar

```


* `whatis`: ম্যান পেজ পড়ার সময় না থাকলে এক লাইনে কুইক সামারি জানার জন্য।
* *উদাহরণ:* `whatis rm` -> `rm (1) - remove files or directories`.


* `alias`: দীর্ঘ অলস কমান্ডকে এক শব্দে নিয়ে আসা।
* *ইউজ কেস (ডকার কন্টেইনার সব এক ক্লিকে ক্লিন করা):*
```bash
alias dclean="docker system prune -a --volumes"

```

---

## সিস্টেম রিসোর্স ও স্টোরেজ মনিটরিং (System Usages)

* `top`: লিনাক্সের ডিফল্ট টাস্ক ম্যানেজার। প্রসেসগুলো কত সিপিইউ আর র্যাম খাচ্ছে তা লাইভ দেখায়। (টার্মিনেট করতে `q` চাপতে হয়)।
* `htop`: `top` এর আধুনিক রূপ।
* *ইউজ কেস:* সার্ভার ক্র্যাশ করার মুখে কোন প্রসেসটি দায়ী তা গ্রাফিক্যাল বার দেখে চেনা। `F6` চেপে মেমোরি অনুযায়ী সর্ট করা যায়, `F9` চেপে সরাসরি ওই হ্যাং হওয়া প্রসেস কিল (Kill) করা যায়।


* `uptime`: সার্ভারটি কত দিন ধরে রিবুট ছাড়া চলছে তা দেখা এবং লোড অ্যাভারেজ (Load Average) ট্র্যাক করা।
* *লোড অ্যাভারেজ ট্রিক:* আউটপুটে ৩টি সংখ্যা থাকে (১ মিনিট, ৫ মিনিট এবং ১৫ মিনিটের লোড)। আপনার সিপিইউ কোর যদি ৪টি হয় আর লোড যদি ৫.০ দেখায়, তার মানে সার্ভার ওভারলোডেড ও স্লো হচ্ছে।


* `df -h -i` (Disk Free):
* `-h`: গিগাবাইটে দেখায়। (যেমন: `df -h` -> /dev/sda1  40G  35G  5G  88% /)
* `-i`: ইনোড স্ট্যাটাস। লিনাক্সে প্রতিটি ফাইলের জন্য ১টি ইনোড লাগে। যদি ডিস্কে ২০ জিবি জায়গাও ফাঁকা থাকে কিন্তু ইনোড ১০০% পূর্ণ হয়ে যায়, তবে সার্ভার বলবে "No space left on device"। সেশন ফাইল বা ক্যাশ ফাইলের আধিক্যের কারণে এটি হয়।


* `free -m`:
* *ইউজ কেস:* মেমোরি লিক চেক করা। র্যামের অবস্থা মেগাবাইটে দেখা। `available` কলামটি খেয়াল করতে হয়, যা দেখে বোঝা যায় নতুন কোনো প্রসেস (যেমন ডকার বা এনগিন্স) চালু করার মতো র্যাম আছে কিনা।


---

## বেসিক টেক্সট এডিটিং

* `nano +20 /etc/nginx/nginx.conf`
* **ইউজ কেস:** যখন সিস্টেম লগ বা কম্পাইলার বলে "Line 20: Syntax Error", তখন ফাইলে ঢুকে স্ক্রোল করে ২০ নম্বর লাইন খোঁজার দরকার নেই। এই কমান্ড সরাসরি কনফিগারেশন ফাইলের ২০ নম্বর লাইনে কার্সার নিয়ে এডিটর ওপেন করবে।



---

## ফাইন্ড টুল (`find`)

ফাইল খোঁজার জন্য এটি লিনাক্সের সবচেয়ে শক্তিশালী জাদুকরী টুল।

* `find /var/log -type f -name "*.log"` -> `/var/log` এর ভেতরের সব ফাইল যার এক্সটেনশন `.log` তা বের করবে।
* `find /home -iname "index.html"` -> কেস-ইনসেন্সিটিভ সার্চ (Index.html, INDEX.HTML সব চলে আসবে)।
* `find . -type d`: শুধুমাত্র ফোল্ডার/ডিরেক্টরিগুলো লিস্ট করবে।
* `find /tmp -type f -size +100M`: ১ মাসের পুরানো বা ১০০ মেগাবাইটের বড় ক্যাশ ফাইল খুঁজে বের করে ডিস্ক খালি করার জন্য টার্গেট করা।
* `find /var/www -user miftah`: নির্দিষ্ট ইউজারের পারমিশনে থাকা ফাইলগুলো আইসোলেট করা।

লিনাক্স (Linux) এবং ইউনিক্স-ভিত্তিক সিস্টেমে ফাইল বা ডিরেক্টরি খুঁজে বের করার জন্য **`find`** কমান্ড সবচেয়ে পাওয়ারফুল ও গুরুত্বপূর্ণ একটি টুল।

বেসিক থেকে অ্যাডভান্সড পর্যন্ত **`find`** কমান্ড ব্যবহারের একটি পূর্ণাঙ্গ গাইড নিচে দেয়া হলো:

---

### ১. Basic Usage (প্রাথমিক ব্যবহার)

`find` কমান্ডের সাধারণ সিনট্যাক্স:

```bash
find [কোথায় খুঁজবেন] [কীভাবে খুঁজবেন/শর্ত] [ফাইল বা ফোল্ডারের নাম]

```

* **বর্তমান ডিরেক্টরিতে নির্দিষ্ট নামের ফাইল খোঁজা:**
```bash
find . -name "filename.txt"

```


*(এখানে `.` নির্দেশ করে বর্তমান ডিরেক্টরি)*
* **কেস-ইনসেনসিটিভ (Case-insensitive) খোঁজা:**
ছোট হাতের বা বড় হাতের অক্ষরের পার্থক্য না রেখে খুঁজতে `-iname` ব্যবহার করা হয়:
```bash
find . -iname "filename.txt"

```


* **নির্দিষ্ট ফোল্ডারের ভেতরে ফোল্ডার বা ফাইল খোঁজা:**
```bash
find /home/user/Documents -name "report.pdf"

```



---

### ২. Intermediate Usage (মধ্যবর্তী পর্যায়)

#### টাইপ অনুযায়ী আলাদা করা (`-type`)

* **শুধু ফাইল (Files) খুঁজতে:**
```bash
find . -type f -name "*.txt"

```


* **শুধু ডিরেক্টরি (Directories/Folders) খুঁজতে:**
```bash
find . -type d -name "project*"

```



#### সাইজ বা আকার অনুযায়ী খোঁজা (`-size`)

* **১০ মেগাবাইটের চেয়ে বড় ফাইল খুঁজতে:**
```bash
find . -type f -size +10M

```


* **১ গিগাবাইটের চেয়ে ছোট ফাইল খুঁজতে:**
```bash
find . -type f -size -1G

```


* **একদম ফাঁকা (Empty) ফাইল বা ফোল্ডার খুঁজতে:**
```bash
find . -empty

```



#### সময় অনুযায়ী খোঁজা (`-mtime`, `-atime`)

* **গত ৭ দিনে পরিবর্তন (Modify) হওয়া ফাইল খুঁজতে:**
```bash
find . -type f -mtime -7

```


* **৩০ দিনের বেশি পুরনো ফাইল খুঁজতে:**
```bash
find . -type f -mtime +30

```



---

### ৩. Advanced Usage (অ্যাডভান্সড পর্যায়)

#### পারমিশন এবং ওনারশিপ অনুযায়ী খোঁজা

* **৭৭৭ (Read, Write, Execute all) পারমিশন থাকা ফাইল খুঁজতে:**
```bash
find . -type f -perm 777

```


* **নির্দিষ্ট কোনো ইউজার (User) বা গ্রুপের ফাইল খুঁজতে:**
```bash
find . -user root

```



#### সার্চের গভীরতা নির্দিষ্ট করা (`-maxdepth`)

সাব-ডিরেক্টরির গভীরে না গিয়ে শুধু প্রথম বা নির্দিষ্ট লেভেল পর্যন্ত খুঁজতে:

```bash
find . -maxdepth 1 -type f -name "*.sh"

```

#### বহুমাত্রিক শর্ত যুক্ত করা (Logical Operators)

* **AND অপারেশন (txt ফাইল এবং ১০০KB এর কম):**
```bash
find . -type f -name "*.txt" -size -100k

```


* **OR অপারেশন (txt অথবা pdf ফাইল):**
```bash
find . -type f \( -name "*.txt" -o -name "*.pdf" \)

```



#### অ্যাকশন চালানো (`-exec`)

`find` দিয়ে খুঁজে পাওয়ার পর সেই ফাইলগুলোর ওপর সরাসরি অন্য কোনো কাজ করা যায়।

* **খুঁজে পাওয়া সব `.tmp` ফাইল মুছে ফেলা:**
```bash
find . -type f -name "*.tmp" -exec rm -f {} \;

```


*(এখানে `{}` প্রতীকটি খুঁজে পাওয়া প্রতিটি ফাইল নির্দেশ করে এবং `\;` কমান্ডের সমাপ্তি বোঝায়)*
* **সব `.sh` ফাইলের পারমিশন পরিবর্তন করা:**
```bash
find . -type f -name "*.sh" -exec chmod +x {} \;

```



---

#### সংক্ষেপে গুরুত্বপূর্ণ চিহ্নের গাইড

| ফ্লাগ       | বিবরণ                              |
| --------- | --------------------------------- |
| `-type f` | শুধুমাত্র ফাইল খুঁজবে                     |
| `-type d` | শুধুমাত্র ডিরেক্টরি খুঁজবে                   |
| `-name`   | ফাইলের নাম মিলিয়ে খুঁজবে (Case sensitive)  |
| `-iname`  | নাম মিলিয়ে খুঁজবে (Case insensitive)     |
| `-size`   | ফাইলের সাইজ অনুযায়ী খুঁজবে (`k`, `M`, `G`) |
| `-mtime`  | মোডিফিকেশনের সময় ধরে খুঁজবে (দিনে)           |
| `-exec`   | খুঁজে পাওয়া ফাইলের ওপর অন্য কমান্ড রান করবে   |

## Bash
```bash
miftah@miftahcoding:~$ htop
miftah@miftahcoding:~$ uptime
 22:11:58 up 5 min,  1 user,  load average: 0.07, 0.16, 0.09
miftah@miftahcoding:~$ uptime
 22:12:15 up 6 min,  1 user,  load average: 0.36, 0.23, 0.11
miftah@miftahcoding:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
tmpfs             692388     2324    690064   1% /run
/dev/vda2       19503340 10265376   8221900  56% /
tmpfs            1730968        0   1730968   0% /dev/shm
efivarfs             256       16       240   7% /sys/firmware/efi/efivars
none                1024        0      1024   0% /run/credentials/systemd-journald.service
none                1024        0      1024   0% /run/credentials/systemd-resolved.service
/dev/vda1         973948     6680    967268   1% /boot/efi
tmpfs            1730968        8   1730960   1% /tmp
none                1024        0      1024   0% /run/credentials/serial-getty@ttyAMA0.service
tmpfs             346192       84    346108   1% /run/user/1000
miftah@miftahcoding:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           677M  2.3M  674M   1% /run
/dev/vda2        19G  9.8G  7.9G  56% /
tmpfs           1.7G     0  1.7G   0% /dev/shm
efivarfs        256K   16K  240K   7% /sys/firmware/efi/efivars
none            1.0M     0  1.0M   0% /run/credentials/systemd-journald.service
none            1.0M     0  1.0M   0% /run/credentials/systemd-resolved.service
/dev/vda1       952M  6.6M  945M   1% /boot/efi
tmpfs           1.7G  8.0K  1.7G   1% /tmp
none            1.0M     0  1.0M   0% /run/credentials/serial-getty@ttyAMA0.service
tmpfs           339M   84K  338M   1% /run/user/1000
miftah@miftahcoding:~$ df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
tmpfs           819200   1182  818018    1% /run
/dev/vda2      1250928 179720 1071208   15% /
tmpfs           432742      1  432741    1% /dev/shm
efivarfs             0      0       0     - /sys/firmware/efi/efivars
none              1024      1    1023    1% /run/credentials/systemd-journald.service
none              1024      1    1023    1% /run/credentials/systemd-resolved.service
/dev/vda1            0      0       0     - /boot/efi
tmpfs          1048576     54 1048522    1% /tmp
none              1024      1    1023    1% /run/credentials/serial-getty@ttyAMA0.service
tmpfs            86548    155   86393    1% /run/user/1000
miftah@miftahcoding:~$ free
               total        used        free      shared  buff/cache   available
Mem:         3461936     2066352      316584      219360     1451240     1395584
Swap:        3163132       21432     3141700
miftah@miftahcoding:~$ free -m
               total        used        free      shared  buff/cache   available
Mem:            3380        2018         309         214        1417        1362
Swap:           3088          20        3068
miftah@miftahcoding:~$ free -h
               total        used        free      shared  buff/cache   available
Mem:           3.3Gi       2.0Gi       310Mi       214Mi       1.4Gi       1.3Gi
Swap:          3.0Gi        20Mi       3.0Gi
miftah@miftahcoding:~$ c

```