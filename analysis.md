#Network Security Scan Analysis
Target : 192.168.1.7(IPV4 Address)
Tools : Nmap 7.92 , Wireshark 3.6.2

-------------------
## 1. Scan Overview 
### Nmap Command
''bash/powershell

nmap -sS -T4 -A -v -p- 192.168.1.7 -oN scan_results.txt
Where -> -sS is TCP SYN Scan which sends SYN Packets to check port status without completing TCP handshake Process.
-> -T4 is Timing Template which scan faster and avoid IDS triggers
-> -A is Aggressive Mode which enables the OS detection (-O) , version detection (-sV), Script Scanning (-sC)
-> -v is verbose which shows the real-time scan progress and additional details
-> -p- is scan all ports it will scan (1-65535) without this Nmap scans only 1000 common ports
-> 192.168.1.7 is the target IP address
-> -oN scan_results.txt is output which saves the results in text format to scan_results.txt

The Scan Results Summary 

Starting Nmap 7.97 ( https://nmap.org ) at 2025-05-26 16:07 +0530
NSE: Loaded 158 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 16:07
Completed NSE at 16:07, 0.00s elapsed
Initiating NSE at 16:07
Completed NSE at 16:07, 0.00s elapsed
Initiating NSE at 16:07
Completed NSE at 16:07, 0.00s elapsed
Initiating Parallel DNS resolution of 1 host. at 16:07
Completed Parallel DNS resolution of 1 host. at 16:07, 0.13s elapsed
Initiating SYN Stealth Scan at 16:07
Scanning LAPTOP-JJA8U8UM.bbrouter (192.168.1.7) [65535 ports]
Discovered open port 135/tcp on 192.168.1.7
Discovered open port 139/tcp on 192.168.1.7
Discovered open port 8080/tcp on 192.168.1.7
Discovered open port 445/tcp on 192.168.1.7
Discovered open port 80/tcp on 192.168.1.7
Discovered open port 57621/tcp on 192.168.1.7
Discovered open port 49666/tcp on 192.168.1.7
Discovered open port 49664/tcp on 192.168.1.7
Discovered open port 49665/tcp on 192.168.1.7
Discovered open port 49670/tcp on 192.168.1.7
Discovered open port 53342/tcp on 192.168.1.7
Discovered open port 49668/tcp on 192.168.1.7
Discovered open port 5040/tcp on 192.168.1.7
Discovered open port 49667/tcp on 192.168.1.7
Completed SYN Stealth Scan at 16:08, 6.22s elapsed (65535 total ports)
Initiating Service scan at 16:08
Scanning 14 services on LAPTOP-JJA8U8UM.bbrouter (192.168.1.7)
Service scan Timing: About 50.00% done; ETC: 16:09 (0:00:34 remaining)
Completed Service scan at 16:09, 83.67s elapsed (14 services on 1 host)
Initiating OS detection (try #1) against LAPTOP-JJA8U8UM.bbrouter (192.168.1.7)
Retrying OS detection (try #2) against LAPTOP-JJA8U8UM.bbrouter (192.168.1.7)
Retrying OS detection (try #3) against LAPTOP-JJA8U8UM.bbrouter (192.168.1.7)
Retrying OS detection (try #4) against LAPTOP-JJA8U8UM.bbrouter (192.168.1.7)
Retrying OS detection (try #5) against LAPTOP-JJA8U8UM.bbrouter (192.168.1.7)
NSE: Script scanning 192.168.1.7.
Initiating NSE at 16:09
Completed NSE at 16:09, 14.25s elapsed
Initiating NSE at 16:09
Completed NSE at 16:09, 0.07s elapsed
Initiating NSE at 16:09
Completed NSE at 16:09, 0.00s elapsed
Nmap scan report for LAPTOP-JJA8U8UM.bbrouter (192.168.1.7)
Host is up (0.00043s latency).
Not shown: 65520 closed tcp ports (reset)
PORT      STATE    SERVICE       VERSION
80/tcp    open     http          Microsoft IIS httpd 10.0
| http-methods:
|   Supported Methods: OPTIONS TRACE GET HEAD POST
|_  Potentially risky methods: TRACE
|_http-title: IIS Windows
|_http-server-header: Microsoft-IIS/10.0
135/tcp   open     msrpc         Microsoft Windows RPC
137/tcp   filtered netbios-ns
139/tcp   open     netbios-ssn   Microsoft Windows netbios-ssn
445/tcp   open     microsoft-ds?
5040/tcp  open     unknown
8080/tcp  open     http          Apache httpd 2.4.63 ((Win64) mod_fcgid/2.3.10-dev)
|_http-title: My Local Server
|_http-open-proxy: Proxy might be redirecting requests
| http-methods:
|   Supported Methods: OPTIONS HEAD GET POST TRACE
|_  Potentially risky methods: TRACE
|_http-server-header: Apache/2.4.63 (Win64) mod_fcgid/2.3.10-dev
49664/tcp open     msrpc         Microsoft Windows RPC
49665/tcp open     msrpc         Microsoft Windows RPC
49666/tcp open     msrpc         Microsoft Windows RPC
49667/tcp open     msrpc         Microsoft Windows RPC
49668/tcp open     msrpc         Microsoft Windows RPC
49670/tcp open     msrpc         Microsoft Windows RPC
53342/tcp open     unknown
| fingerprint-strings:
|   NULL:
|_    {"type":"Tier1","version":"1.0"}
57621/tcp open     unknown
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port53342-TCP:V=7.97%I=7%D=5/26%Time=68344488%P=i686-pc-windows-windows
SF:%r(NULL,22,"{\"type\":\"Tier1\",\"version\":\"1\.0\"}\r\n");
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.97%E=4%D=5/26%OT=80%CT=1%CU=33841%PV=Y%DS=0%DC=L%G=Y%TM=683444F
OS:4%P=i686-pc-windows-windows)SEQ(SP=100%GCD=1%ISR=10C%TI=I%CI=I%II=I%SS=S
OS:%TS=A)SEQ(SP=101%GCD=1%ISR=10A%TI=I%CI=I%II=I%SS=S%TS=A)SEQ(SP=102%GCD=1
OS:%ISR=10C%TI=I%CI=I%II=I%SS=S%TS=A)SEQ(SP=107%GCD=1%ISR=10D%TI=I%CI=I%II=
OS:I%SS=S%TS=A)SEQ(SP=FD%GCD=1%ISR=10C%TI=I%CI=I%II=I%SS=S%TS=A)OPS(O1=MFFD
OS:7NW8ST11%O2=MFFD7NW8ST11%O3=MFFD7NW8NNT11%O4=MFFD7NW8ST11%O5=MFFD7NW8ST1
OS:1%O6=MFFD7ST11)WIN(W1=FFFF%W2=FFFF%W3=FFFF%W4=FFFF%W5=FFFF%W6=FFFF)ECN(R
OS:=Y%DF=Y%T=80%W=FFFF%O=MFFD7NW8NNS%CC=N%Q=)T1(R=Y%DF=Y%T=80%S=O%A=S+%F=AS
OS:%RD=0%Q=)T2(R=Y%DF=Y%T=80%W=0%S=Z%A=S%F=AR%O=%RD=0%Q=)T3(R=Y%DF=Y%T=80%W
OS:=0%S=Z%A=O%F=AR%O=%RD=0%Q=)T4(R=Y%DF=Y%T=80%W=0%S=A%A=O%F=R%O=%RD=0%Q=)T
OS:5(R=Y%DF=Y%T=80%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=80%W=0%S=A%A=
OS:O%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=80%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF
OS:=N%T=80%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=Z%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=80
OS:%CD=Z)

Uptime guess: 8.007 days (since Sun May 18 15:59:58 2025)
Network Distance: 0 hops
TCP Sequence Prediction: Difficulty=263 (Good luck!)
IP ID Sequence Generation: Incremental
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-time:
|   date: 2025-05-26T10:39:35
|_  start_date: N/A
| smb2-security-mode:
|   3.1.1:
|_    Message signing enabled but not required

NSE: Script Post-scanning.
Initiating NSE at 16:09
Completed NSE at 16:09, 0.00s elapsed
Initiating NSE at 16:09
Completed NSE at 16:09, 0.00s elapsed
Initiating NSE at 16:09
Completed NSE at 16:09, 0.00s elapsed
Read data files from: C:\Program Files (x86)\Nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 115.39 seconds
           Raw packets sent: 65616 (2.891MB) | Rcvd: 131284 (5.521MB)

------------------------------------------

#### 2. Wireshark Traffic Analysis
-> Select the WiFi for present interfaces so that we will get all the TCP , Source and Destination address 
-> To check how many bytes have sent between source and destination , go to statistics and in that go to conversations so that we will get to know how mant TCP ports have sent and UDP too. 


