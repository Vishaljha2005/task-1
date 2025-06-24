Network Scan & Security Analysis Report

1. Nmap Installation
- Status: Successfully installed from the official website: [Nmap Download](https://nmap.org/download.html).
- Operating System: [Your OS Here]
- Command (Linux): 
  sudo apt install nmap

2. Identifying Local IP Range
- Method: Used ipconfig (Windows) or ifconfig/ip a (Linux/macOS).
- Example Result: 
  - IP: 192.168.1.12
  - Subnet: 255.255.255.0 
  - Range: 192.168.1.0/24

3. Nmap TCP SYN Scan
- Command: 
  nmap -sS 192.168.1.0/24
- Summary of Results:
  - 192.168.1.1 - Ports: 80, 443 (HTTP, HTTPS)
  - 192.168.1.5 - Ports: 22, 80 (SSH, HTTP)
  - 192.168.1.10 - Ports: 21, 23, 80 (FTP, Telnet, HTTP)

4. Noted Open Ports
- All active hosts and their ports were documented as shown above.

5. Wireshark Packet Capture (Optional)
- Tool Used: Wireshark on active interface.
- Filters: 
  - ip.addr == 192.168.1.5
  - tcp.port == 80
- Observation: TCP SYN packets observed with normal handshakes.

6. Research on Common Services
- Port 21: FTP (Insecure)
- Port 22: SSH (Secure login)
- Port 23: Telnet (Insecure)
- Port 80: HTTP
- Port 443: HTTPS

7. Identifying Security Risks
- Insecure Protocols: 
  - Telnet and FTP should be avoided.
- SSH Security: 
  - Use strong keys for SSH.
- HTTP to HTTPS: 
  - Upgrade all HTTP services to HTTPS.
- Port Management: 
  - Close all unused ports.

8. Scan Result Saved
- Commands Used: 
  nmap -sS 192.168.1.0/24 -oN network_scan.txt
  nmap -sS 192.168.1.0/24 -oX network_scan.xml
- HTML Generation: 
  xsltproc /usr/share/nmap/nmap.xsl network_scan.xml -o network_scan.html

Conclusion
- Summary: The scan identified several open ports.
- Recommendations: 
  - Disable unused services.
  - Use encryption for secure communications.
  - Regularly update services to mitigate vulnerabilities.
