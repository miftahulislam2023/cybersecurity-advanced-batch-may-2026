# Class 22
## Computer Network Fundamentals Part 4

## Wireshark
- It is a free and open-source packet analyzer.

## PDUs
- Layer 1: Bits (or Bytes) -> OK
- Layer 2: Ethernet Frame, WiFi MAC Frame
- Layer 3: IP Packet
- Layer 4: TCP Segment, UDP Datagram
- Layer 5-7: Data (or Message)

## Draw.io
- Draw.io is a free and open-source online diagramming tool.
- [Click here to open Draw.io](https://app.diagrams.net/)

## Study
1. Dial-up internet vs broadband 

### Ports
- Max 65536 ports (2^16)
- Well-Known Ports (0–1023)
- Registered Ports (1024–49151)
- Dynamic / Private Ports / Empheral Ports (49152–65535)

### Recon
- empirepremiumbd@gmail.com
- +880 1349-867710
- empirepremium.store

### empirepremium.store
1. Technology
   1. Wordpress
2. DNS
   1. IP -> 103.112.62.103 (base domain)
   2. WHOIS
   ```
    Registrar WHOIS Server: whois.atakteknoloji.com
    Registrar URL: https://www.atakdomain.com
    Updated Date: 2026-10-10T16:22:00.486Z
    Creation Date: 2026-10-05T16:20:58.650Z
    Registry Expiry Date: 2027-10-05T16:20:58.650Z
    Registrar: Atak Domain Bilgi Teknolojileri A.Ş.
    Registrar IANA ID: 1601
    Registrar Abuse Contact Email: domain@apiname.com
    Registrar Abuse Contact Phone: +90.5327135505
    Domain Status: clientTransferProhibited https://icann.org/epp#clientTransferProhibited
    Name Server: dns1.mycloudsweb.com
    Name Server: dns2.mycloudsweb.com
    ```
   3. 99it
    Location	Bangladesh National University, Dhaka, Bangladesh
    AS	AS150156
    AS name	99it
3. https://www.empirepremium.store/wp-login.php?redirect_to=https%3A%2F%2Fempirepremium.store%2Fwp-admin%2F&reauth=1
   
### ASCII (American Standard Code for Information Interchange)

### Wireshark Packet Analysis
```bash
0000   a2 9a 8e 40 7f 64 12 9b ae fc f8 dc 08 00 45 00   ...@.d........E.
0010   00 3c 75 a4 40 00 40 11 c3 b3 c0 a8 40 07 c0 a8   .<u.@.@.....@...
0020   40 01 8c 2f 00 35 00 28 55 5a 8d de 01 00 00 01   @../.5.(UZ......
0030   00 00 00 00 00 00 03 77 77 77 06 67 6f 6f 67 6c   .......www.googl
0040   65 03 63 6f 6d 00 00 01 00 01                     e.com.....
```
- Total Length: 74 bytes
- 16 bytes: ```a2 9a 8e 40 7f 64 12 9b ae fc f8 dc``` -> destination MAC and source MAC
- 2 bytes: ```08 00``` -> Type: IPv4 (0800)
- 1 byte: ```45``` -> Version: 4, Header Length: 5
- 2 bytes: ```00 3c``` -> Total Length: 60 bytes
- 2 bytes: ```75 a4``` -> ID: 30660
- 2 bytes: ```40 00``` -> Flags: 0, Fragment Offset: 0
- 1 byte: ```40``` -> TTL: 64
- 1 byte: ```11``` -> Protocol: TCP
- 2 bytes: ```c3 b3``` -> Checksum: 50131
- 4 bytes: ```c0 a8 40 07``` -> Source IP: [IP_ADDRESS]
- 4 bytes: ```c0 a8 40 01``` -> Destination IP: [IP_ADDRESS]
- 2 bytes: ```8c 2f``` -> Source Port: 35343
- 2 bytes: ```00 35``` -> Destination Port: 53
- 2 bytes: ```00 28``` -> Length: 40 bytes
- 4 bytes: ```55 5a 8d de``` -> Sequence Number: 1434484958
- 4 bytes: ```01 00 00 01``` -> Acknowledgment Number: 1
- 2 bytes: ```00 00``` -> Data Offset: 8
- 2 bytes: ```00 00``` -> Flags: 0
- 2 bytes: ```10 00``` -> Window Size: 4096
- 2 bytes: ```8b 20``` -> Checksum: 35584
- 2 bytes: ```00 00``` -> Urgent Pointer: 0
- 40 bytes: ```00 03 77 77 77 06 67 6f 6f 67 6c 65 03 63 6f 6d 00 00 01 00 01``` -> DNS Name
  - ```06 67 6f 6f 67 6c 65``` -> google
  - ```03 63 6f 6d``` -> com
  - ```00``` -> Root
  - ```00 01``` -> Query Type: A Record
  - ```00 01``` -> Query Class: IN (Internet)

