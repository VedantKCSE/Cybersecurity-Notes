---
icon: folder-magnifying-glass
---

# Reconnaissance Phase

#### 1. **Enumerating Domains with Subfinder**

*   Enumerate subdomains using `subfinder`:

    ```bash
    subfinder -d hackerone.com -o subfind.txt
    ```

#### 2. **Gathering Open Information with TheHarvester**

*   Collect publicly available information:

    ```bash
    theharvester -d hackerone.com
    ```
* **Note**: TheHarvester setup may be required.

#### 3. **Active Enumeration with Knockpy**

*   Perform active enumeration and brute force:

    ```bash
    knockpy -d hackerone.com --recon --bruteforce > knock_enum.txt
    ```

#### 4. **AnalyticsRelationships Tool**

*   Use `AnalyticsRelationships` to analyze relationships:

    ```bash
    python3 analyticsrelationships.py -u https://www.example.com > /tmp/example.txt
    ```
*   Set up for global use:

    ```bash
    #!/usr/bin/env python3
    chmod +x analyticsrelationships.py
    sudo mv analyticsrelationships.py /usr/bin/ar
    source ~/.bashrc
    ```
*   Command execution:

    ```bash
    ar -u https://www.example.com
    ```

#### 5. **Data Cleaning**

*   Extract required data using `awk`:

    ```bash
    awk '/^\|__/ {print $2}' [input file] > [output file]
    ```
* Combine commands using pipes if needed.

#### 6. **Checking Active Domains with Httpx**

*   Verify domains are active:

    ```bash
    httpx-toolkit -l subfind.txt -mc 200
    ```
*   Retrieve IP addresses:

    ```bash
    httpx-toolkit -l subfind.txt -ip -silent | grep -oP '\[\K[^\]]+' > ip_addr.txt
    ```

#### 7. **Finding Open Ports with Naabu**

*   Scan for open ports:

    ```bash
    sudo naabu -l ip_addr.txt > op_ports.txt
    ```

#### 8. **Discovering Endpoints with Dirsearch**

*   Perform directory brute-forcing:

    ```bash
    dirsearch -u https://hackerone.com -w /usr/share/wordlists/dirb/big.txt -R 4 > dirsearch.txt
    ```

***

### Additional Tools

#### 1. **Katana**

*   **Installation**:

    ```bash
    sudo apt install golang -y
    go install github.com/projectdiscovery/katana/cmd/katana@latest
    sudo cp ~/go/bin/katana /bin/
    ```
*   **Usage**:

    ```bash
    katana -u https://www.hackerone.com/ > crawl_katana.txt
    ```

#### 2. **Hakrawler**

*   **Installation**:

    ```bash
    sudo apt install docker.io -y
    git clone https://github.com/hakluke/hakrawler
    cd hakrawler
    sudo docker build -t hakluke/hakrawler .
    ```
*   **Usage**:

    ```bash
    sudo docker run --rm -i hakluke/hakrawler --help
    ```

#### 3. **Subjs**

*   **Installation**:

    ```bash
    tar xvf subjs_1.0.1_linux_amd64.tar.gz
    sudo mv subjs /usr/bin/subjs
    ```

#### 4. **Spiderfoot**

*   Start Spiderfoot:

    ```bash
    spiderfoot -l localhost:5009
    ```
* Open the provided link in a browser.

#### 5. **Linkfinder**

*   **Installation**:

    ```bash
    git clone https://github.com/GerbenJavado/LinkFinder.git
    cd LinkFinder
    sudo pip install jsbeautifier
    ```
*   **Usage**:

    ```bash
    python3 linkfinder.py -i https://www.hackerone.com -o cli
    ```
*   **Finding links recursively**:

    ```bash
    while read url; do
        python3 linkfinder.py -i "$url" -o cli > [output file]
    done < [input file]
    ```
