# Class 17

## nmap
- Nmap (Network Mapper-এর সংক্ষিপ্ত রূপ) হলো নেটওয়ার্ক ডিসকভারি এবং সিকিউরিটি অডিটিংয়ের জন্য ব্যবহৃত একটি ওপেন-সোর্স টুল। টার্গেট ডিভাইসে বিশেষভাবে তৈরি প্যাকেট পাঠিয়ে এবং সেগুলোর রেসপন্স বিশ্লেষণ করে এটি নেটওয়ার্কের বিভিন্ন ডিভাইস, ওপেন পোর্ট, সার্ভিস এবং সম্ভাব্য নিরাপত্তা দুর্বলতা শনাক্ত করতে সাহায্য করে। Nmap একটি নেটওয়ার্কের কাঠামো এবং বর্তমান অবস্থা সম্পর্কে বিস্তারিত তথ্য প্রদান করে।

**সতর্কবার্তা (Disclaimer):** Nmap শুধুমাত্র আপনার নিজস্ব নেটওয়ার্কে অথবা যে নেটওয়ার্ক স্ক্যান করার অনুমতি আপনার আছে, সেখানে ব্যবহার করা উচিত। এই ব্যবহারিক ল্যাবের জন্য আমরা **scanme.nmap.org** ব্যবহার করব, যা Nmap সিকিউরিটি স্ক্যানার প্রজেক্টের পক্ষ থেকে শিক্ষামূলক উদ্দেশ্যে উন্মুক্ত রাখা একটি ফ্রি সার্ভিস। ওয়েবসাইটের নির্দেশনা অনুযায়ী, ব্যবহারকারীরা Nmap বা অন্যান্য পোর্ট স্ক্যানার দিয়ে এই হোস্টে স্ক্যান করতে পারবেন; তবে স্ক্যানের সংখ্যা দিনে মাত্র কয়েকটিতে সীমাবদ্ধ রাখা উচিত এবং ব্রুট-ফোর্স বা ঘনঘন উচ্চমাত্রার স্ক্যানিং এড়িয়ে চলা উচিত।

---

**বেসিক Nmap স্ক্যান (Basic Nmap scan)**

* **ধাপ ১:** আপনার Kali Linux ভার্চুয়াল মেশিন চালু করুন।
* **ধাপ ২:** টার্মিনাল খুলুন।
* **ধাপ ৩:** লিখুন:

```bash
nmap scanme.nmap.org

```

> **নোট:** যদি `nmap scanme.nmap.org` কমান্ডটি সম্পন্ন হতে স্বাভাবিকের চেয়ে বেশি সময় নেয়, তবে স্ক্যান দ্রুত করতে আপনি `nmap -T4 -F -n scanme.nmap.org` ব্যবহার করতে পারেন। এটি টাইমিং বাড়িয়ে, কম পোর্ট স্ক্যান করে এবং DNS রেজোলিউশন বন্ধ রেখে স্ক্যান দ্রুত সম্পন্ন করে।

* **ধাপ ৪:** আউটপুট বিশ্লেষণ করুন:
* **Port:** টার্গেট মেশিনের কোনো সার্ভিস বা অ্যাপ্লিকেশনের যোগাযোগের নির্দিষ্ট চ্যানেলটি শনাক্ত করে।
* **State:** পোর্টটি open (সক্রিয় এবং সম্ভাব্য ঝুঁকিপূর্ণ), closed (নিষ্ক্রিয়), নাকি filtered (ফায়ারওয়াল বা অন্য নিরাপত্তা ব্যবস্থার মাধ্যমে সুরক্ষিত) তা নির্দেশ করে।
* **Service:** ওপেন পোর্টে কোন অ্যাপ্লিকেশন বা প্রোটোকল চলছে তা শনাক্ত করে।



---

**বিস্তারিত Nmap স্ক্যান (Detailed Nmap scan)**

* **ধাপ ১:** লিখুন:

```bash
nmap -sV scanme.nmap.org

```

> **নোট:** যদি `nmap -sV scanme.nmap.org` কমান্ডটি সম্পন্ন হতে বেশি সময় নেয়, তবে আপনি `nmap -T4 -F -n -sV scanme.nmap.org` ব্যবহার করতে পারেন। এটি টাইমিং বাড়িয়ে, সাধারণ পোর্টগুলোর মধ্যে স্ক্যান সীমাবদ্ধ রেখে এবং DNS রেজোলিউশন বাদ দিয়েও সার্ভিস ভার্সন শনাক্ত করে কার্যকরভাবে সময় কমিয়ে আনে।

* **ধাপ ২:** আউটপুট বিশ্লেষণ করুন:
* **Port:** বেসিক স্ক্যানের মতোই পোর্টের তথ্য প্রদান করে।
* **State:** বেসিক স্ক্যানের মতোই পোর্টের অবস্থার তথ্য প্রদান করে।
* **Service:** প্রতিটি পোর্টে চলমান সার্ভিস শনাক্ত করতে বিস্তারিত বিশ্লেষণ চালায়, যা সাধারণত আরও নিখুঁত ফলাফল দেয়।
* **Version:** ওপেন পোর্টে চলমান সার্ভিস বা অ্যাপ্লিকেশনের নির্দিষ্ট ভার্সন শনাক্ত করার জন্য সক্রিয়ভাবে ডেটা পাঠায়।



---

**অ্যাগ্রেসিভ Nmap স্ক্যান (Aggressive Nmap scan)**

* **ধাপ ১:** লিখুন:

```bash
nmap -A scanme.nmap.org

```

> **নোট:** এটি সম্পন্ন হতে কয়েক মিনিট সময় লাগে। যদি `nmap -A scanme.nmap.org` কমান্ডটি অতিরিক্ত সময় নেয়, তবে আপনি `nmap -T4 -F -n -A scanme.nmap.org` ব্যবহার করতে পারেন। এটি টাইমিং বাড়িয়ে, সীমিত পোর্টে স্ক্যান করে এবং DNS রেজোলিউশন বাদ দিয়েও অ্যাগ্রেসিভ ডিটেকশন সম্পন্ন করে স্ক্যানের সময় কমায়।

* **ধাপ ২:** আউটপুট বিশ্লেষণ করুন:
* **Port:** পোর্টের তথ্য প্রদান করে।
* **State:** পোর্টের অবস্থার তথ্য প্রদান করে।
* **Service:** প্রতিটি পোর্টের সার্ভিস বিস্তারিতভাবে নিশ্চিত ও বিশ্লেষণ করে।
* **Version:** সার্ভিসের সঠিক ভার্সন শনাক্তকরণের ওপর কাজ করে।
* **Operating system fingerprinting:** স্ক্যান চলাকালীন আচরণ পর্যবেক্ষণের ওপর ভিত্তি করে টার্গেট সিস্টেমে কোন অপারেটিং সিস্টেম (OS) চলছে তার একটি সম্ভাব্য ধারণা প্রদান করে।
* **Traceroute:** স্ক্যানিং মেশিন থেকে টার্গেট ডিভাইস পর্যন্ত নেটওয়ার্ক পাথ ম্যাপ করে এবং মাঝে কতগুলো নেটওয়ার্ক হপ (hop) রয়েছে তা শনাক্ত করে।

## Important Notes
1. Nmap uses raw IP packets in novel ways to determine
    1. What **hosts** are available on the network, 
    2. What **services** (application name and version) those hosts are offering, 
    3. What **operating systems** (and OS versions) they are running
    4. What type of **packet filters/firewalls** 
2. The state is either-
   1. open - Open means that an application on the target machine is listening for connections/packets on that port
   2. filtered - Filtered means that a firewall, filter, or other network obstacle is blocking the port so that Nmap cannot tell whether it is open or closed
   3. closed - Closed ports have no application listening on them, though they could open up at any time
   4. unfiltered - Ports are classified as unfiltered when they are responsive to Nmap's probes, but Nmap cannot determine whether they are open or closed. 
> `Nmap reports the state combinations open|filtered and closed|filtered when it cannot determine which of the two states describe a port.`

> A typical Nmap scan is shown in Example 1. The only Nmap arguments used in this example are `-A`, to enable OS and version detection, script scanning, and traceroute; `-T4` for faster execution; and then the hostname.

#### Example 1. A representative Nmap scan

```bash
nmap -A -T4 scanme.nmap.org
Nmap scan report for scanme.nmap.org (74.207.244.221)
Host is up (0.029s latency).
rDNS record for 74.207.244.221: li86-221.members.linode.com
Not shown: 995 closed ports
PORT     STATE    SERVICE     VERSION
22/tcp   open     ssh         OpenSSH 5.3p1 Debian 3ubuntu7 (protocol 2.0)
| ssh-hostkey: 1024 8d:60:f1:7c:ca:b7:3d:0a:d6:67:54:9d:69:d9:b9:dd (DSA)
|_2048 79:f8:09:ac:d4:e2:32:42:10:49:d3:bd:20:82:85:ec (RSA)
80/tcp   open     http        Apache httpd 2.2.14 ((Ubuntu))
|_http-title: Go ahead and ScanMe!
646/tcp  filtered ldp
1720/tcp filtered H.323/Q.931
9929/tcp open     nping-echo  Nping echo
Device type: general purpose
Running: Linux 2.6.X
OS CPE: cpe:/o:linux:linux_kernel:2.6.39
OS details: Linux 2.6.39
Network Distance: 11 hops
Service Info: OS: Linux; CPE: cpe:/o:linux:kernel

TRACEROUTE (using port 53/tcp)
HOP RTT      ADDRESS
[Cut first 10 hops for brevity]
11  17.65 ms li86-221.members.linode.com (74.207.244.221)

Nmap done: 1 IP address (1 host up) scanned in 14.40 seconds
```

## TCP vs UDP
1. Use cases
2. Difference

## TCP Three-way handshake
- It happens before data transfer begins
- Three steps
  - SYN -> Synchronize
  - SYN-ACK -> Synchronize Acknowlegde
  - ACK -> Acknowlegde