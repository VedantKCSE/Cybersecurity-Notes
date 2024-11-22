---
description: >-
  Learn how to use Nmap to discover live hosts, find open ports, and detect
  service versions.
icon: diagram-project
---

# Nmap: The Basics

IP Range:&#x20;

```bash
nmap 10.10.134.172-183
```

IP Subnet: 10.10.134.1/24 \~ 10.10.134.0-255&#x20;

```bash
nmap 10.10.134.1/24 ~ 10.10.134.0-255 
```

Hostname:&#x20;

```bash
google.thm
```

{% hint style="info" %}
By default Nmap scans top 1000 ports
{% endhint %}

## Basic Scans

### Ping Scan

```bash
nmap -sn [IP]
```

When scanning a directly connected network, Nmap starts by sending ARP requests. When a device responds to the ARP request, Nmap labels it with “Host is up”.

### List scan

```bash
nmap -sL [IP]
```

### Connect Scan / TCP Scan

```bash
nmap -sT [IP]:
```

connect scan tries TCP 3-way handshake to the specified IP and if connects it is displayed

### SYN Scan (stealth)

```bash
nmap -sS [IP]
```

&#x20;it does a TCP 3-way handshake sends a SYN but never returns ACK, the handshake is never actually completed, it creates less logs and is basically stealth.

### UDP Scan

```bash
nmap -sU [IP]
```

scans for any UDP Ports

## Options

-F: Fast Scan scans the top 100 ports by default

-P\[range], -p-10-1024: scan for the given port range

-o: OS Scan used to scan for probale OS detection

-sV: Version Scan target ka probabale version cahiye toh

-A: Aggressive This option enables OS detection, version scanning, and traceroute, among other things.

-T: Time Required for scan how fast the scan should be ranges from 0-4

\--min-parallelism , --max-parallelism : this helps when network is performing poorly to control the rate of probing of TCP & UDP Packets

\--min-rate , --max-rate : they can control the minimum and maximum rates at which nmap sends packets.

\--host-timeout: Maximum amount of time to wait for a target host

-v: verbose mode this displays the real time progress of an on-going nmap scan, increase the verbosity levels by adding more and more v's

-d: Debugging Level this gives you debugging levels of outputs

-oN - Normal output -oX - XML output -oG - grep-able output (useful for grep and awk) -oA - Output in all major formats
