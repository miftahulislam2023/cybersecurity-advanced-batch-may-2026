# Class 14

## 1. Network Interfaces & IP Configuration

### Interface Management
- `ifdown eth0`: Disables/brings down the network interface `eth0`.
- `ifup eth0`: Enables/brings up the network interface `eth0`.
- `service network restart`: Restarts the overall network service to apply new configurations across network interfaces.

### Interface Display & Diagnostics
- `ifconfig`: Stands for **Interface Configuration**. Used to display and manage active network interface parameters.
- `ip addr show`: Modern Linux command (`iproute2` suite) to display IP addresses and details assigned to all active network interfaces.

---

## 2. Name Resolution & DNS Management

### Name Resolution Architecture
Name resolution on a Linux host translates human-readable domain names into IP addresses. It relies on **three critical files**:

1. **/etc/hosts**: Local static table mapping IP addresses to domain names.
2. **/etc/resolv.conf**: Contains the IP address(es) of the DNS recursive resolver servers.
3. **/etc/nsswitch.conf**: Configures the order of lookup sources (e.g., whether to check `/etc/hosts` first or query DNS via `/etc/resolv.conf`).

### Host & DNS Lookup Commands
- **`host`**: Queries DNS to associate a hostname with an IP address (and vice versa).
  - `host google.com`: Standard forward DNS lookup for `google.com`.
  - `host -t CNAME example.com`: Queries canonical name (alias) records for `example.com`.
  - `host -t SOA example.com`: Queries Start of Authority record for details about the primary DNS zone.
  - `host -a example.com`: Displays all available DNS records for `example.com`.

- **`dig`**: Used to perform detailed DNS server queries and test DNS server functionality to confirm whether the required DNS records are available.

---

## 3. Network Routing & Neighbor Discovery

### Routing Tables
Commands used to display or modify the kernel routing table:
- `route` / `route -n`: Displays the routing table (`-n` prevents name resolution and shows IP addresses numerically).
- `ip route` / `ip route show`: Modern alternative to display network routes using the `iproute2` toolset.

### Neighbor / Address Resolution Protocol (ARP)
- `arp`: Displays and manipulates the system's ARP cache, which maps IPv4 addresses to physical MAC addresses on the local network segment.

---

## 4. Network Connectivity & Diagnostics

### ICMP Reachability
- `ping -c 4 google.com`: Sends ICMP ECHO_REQUEST packets to determine if `google.com` is reachable. Limits output to 4 packets.

> **Important Security Note on Ping:**  
> A failed `ping` command does **not** definitively prove that a remote host is unreachable or down. System administrators frequently configure firewalls and servers to drop ICMP ping requests to mitigate **Denial of Service (DoS)** attacks, where servers are overwhelmed with flood traffic. Thus, `ping` is reliable for local network testing, but may give false negatives on external hosts.

---

## 5. Network Connections, Ports & Socket Statistics

### Ports & Services Concept
A **port** is a unique numeric identifier associated with a network service running on a host. If a port status is **LISTEN**, the associated service is active and ready to accept incoming network connections from remote hosts.

### Connection & Port Analysis Tool: `netstat`
- `netstat`: A versatile network tool providing details on connections, routing tables, and interface statistics.
- `netstat -i`: Displays a table of all network interfaces and packet statistics.
- `netstat -r`: Displays the kernel routing table (similar to `route`).
- `netstat -tln`: Displays listening sockets numerically.
  - `-t`: Filter for TCP sockets.
  - `-l`: Filter for listening sockets.
  - `-n`: Show numeric ports and IP addresses (avoids slow hostname resolution).

### Modern Socket Analysis Tool: `ss`
- **`ss`**: Socket Statistics utility designed as a modern replacement for `netstat`. Supports all major packet and socket types, offers superior execution speed, and provides detailed diagnostic output.
- Primary use case: Inspecting active network connections, statistics, socket states, and data traffic between local and remote hosts.
- `ss -s`: Displays summary statistics for all current network sockets.

---

## 6. Remote Management & SSH Access

### Secure Shell (`ssh`)
Allows users to securely connect to a remote host across a network, authenticate, and execute commands via a terminal session.

### Usage Syntax
- `ssh hostname_or_ip`: Connects to `hostname_or_ip` using the **currently logged-in local username**.
- `ssh username@hostname`: Explicitly specifies a different `username` for authentication on the remote host.