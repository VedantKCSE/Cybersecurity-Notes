---
icon: layer-group
---

# Offline Session Task

## Reconn Phase

use subfinder to enumerate domains

{% embed url="https://projectdiscovery.io/blog/do-you-really-know-subfinder-an-in-depth-guide-to-all-features-of-subfinder-beginner-to-advanced" %}

```bash
subfinder -d hackerone.com -o subfind.txt
```

use havester to get open information available over iternet - setup needed

{% embed url="https://github.com/laramies/theharvester" %}

```
theharvester -d hackerone.com
```

Use Knockpy to get quick bactive enum of sub-domains

{% embed url="https://github.com/guelfoweb/knock" %}

```bash
knockpy -d hackerone.com --recon --bruteforce > knock_enum.txt
```

use [AnalyticsRelationships](https://github.com/Josue87/AnalyticsRelationships)

{% embed url="https://github.com/Josue87/AnalyticsRelationships" %}

```bash
python3 analyticsrelationships.py -u https://www.example.com > /tmp/example.txt
```

use ar globally

```
#!/usr/bin/env python3
```

add this shebang to analyticsrelationships.py, and give the needed permissions (use sudo if permission denied)

```
chmod +x analyticsrelationships.py
sudo mv analyticsrelationships.py /usr/bin/ar
source ~/.bashrc
ar -u https://www.example.com
```

data cleaning

```bash
awk '/^\|__/ {print $2}' [input file] > [output file] 
```

both can be piped together

use httpx-toolkit to see if the domain are up or not

```bash
httpx-toolkit -l subfind.txt -mc 200
```

to get the ip address of the sub domains

```bash
httpx-toolkit -l subfind.txt -ip -silent | grep -oP '\[\K[^\]]+' > ip_addr.txt
```

use naabu to find open ports

```bash
sudo naabu -l ip_addr.txt > op_ports.txt
```

use dirsearch to discover endpoints

```bash
dirsearch -u https://hackerone.com -w /usr/share/wordlists/dirb/big.txt -R 4 > dirsearch.txt
```

katana Installation

```bash
go version
sudo apt install golang -y
go install github.com/projectdiscovery/katana/cmd/katana@latest
sudo cp ~/go/bin/katana /bin/
katana -version
```

katana usage

```bash
katana -u https://www.hackerone.com/ > crawl_katana.txt
```

Subjs Installation

```bash
tar xvf subjs_1.0.1_linux_amd64.tar.gz
sudo mv subjs /usr/bin/subjs 
```

