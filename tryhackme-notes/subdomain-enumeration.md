---
description: >-
  Learn the various ways of discovering subdomains to expand your attack surface
  of a target.
icon: diagram-subtask
---

# Subdomain Enumeration

{% embed url="https://tryhackme.com/r/room/subdomainenumeration" %}
Subdomain Enumeration
{% endembed %}

***

## Notes:

Finding Valid subdomain to expand our attack surface and discover more potential points of Vuln.

### 3 Ways to do it:

1. Brute Force
2. OSINT
3. Virtual Host

### OSINT

1. SSL  / TLS Certificates
2. Search Engines

```bash
site:*.tryhackne.com -site:www.tryhackme.com
```

3. Sublist3r

```bash
./sublist3r.py -d TARGET
```

### Brute Force

* dnsrecon

### Virtual Host

Some times the DNS server are also private and hard to discover as dnsrecon we can use `fuff` to get these various hosts and subdomains

* dnsrecon
* ffuf

***

### Resource Links:

{% embed url="https://crt.sh/" %}
SSL / TLS Certs Log Viewer
{% endembed %}

{% embed url="https://github.com/aboul3la/Sublist3r" %}
