Network Port Scan with Nmap
This project demonstrates a comprehensive network reconnaissance using Nmap to identify open ports, running services, and potential vulnerabilities on a target host (192.168.1.7)
so here are some use cases :
-> Security auditing
-> Vulnerability assessment
->Network troubleshooting
By using a command we can run the scan with in bash/powershell
nmap -sS -T4 -A -v -p- 192.168.1.7 -oN scan_results.txt
