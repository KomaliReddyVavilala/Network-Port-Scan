# Network Port Scanner with Nmap

This project demonstrates comprehensive network reconnaissance using Nmap to identify:
- Open ports and running services
- Service versions and operating system details
- Potential security vulnerabilities

## Target Host
192.168.1.7 i.e., IPV4 Address
## Use Cases
-  Security auditing
-  Vulnerability assessment
-  Network troubleshooting
-  Penetration testing documentation

## Quick Start
Run the scan with:
```bash
nmap -sS -T4 -A -v -p- 192.168.1.7 -oN scan_results.txt
