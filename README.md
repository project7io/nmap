### nmap
 Project7 nmap notes -- Best viewed as a GitHub page  https://project7io.github.io/nmap/

###### Formatting - Make your nmap scans more readable.
Download the nmap stylesheet.
`wget https://raw.githubusercontent.com/honze-net/nmap-bootstrap-xsl/master/nmap-bootstrap.xsl`

Use the nmap stylesheet in your nmap scan. Use -oX to output to XML which is needed for the styelsheet.
`nmap -sS -T4 -A -sC -oX nmapScan.xml --stylesheet nmap-bootstrap.xsl 192.168.0.1`

Optional convert the scan XML to HTML
`xsltproc -o nmapScan.html nmap-bootstrap.xsl nmapScan.xml`

### Install nmap-vulners NSE scripts to quickly detect vulnerabilities

`cd && git clone https://github.com/vulnersCom/nmap-vulners.git`

###### Scan with nmap-vunlers
`nmap --script nmap-vulners -sV -F ###.###.###.###  (-F is for fast scan. -p 0-10000 or define ports)`

###### Example results:
```
Nmap scan report for 10.0.2.7/r
Host is up (0.00050s latency).
Not shown: 999 filtered ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 6.7 (protocol 2.0)
| vulners: 
|   cpe:/a:openbsd:openssh:6.7: 
|     	CVE-2018-15919	5.0	https://vulners.com/cve/CVE-2018-15919
|     	CVE-2017-15906	5.0	https://vulners.com/cve/CVE-2017-15906
|     	CVE-2016-10708	5.0	https://vulners.com/cve/CVE-2016-10708
|     	CVE-2016-0778	4.6	https://vulners.com/cve/CVE-2016-0778
|_    	CVE-2016-0777	4.0	https://vulners.com/cve/CVE-2016-0777
MAC Address: 08:00:27:10:B8:D0 (Oracle VirtualBox virtual NIC)
```
##### With bootstrap formatting
`nmap --script nmap-vulners -sV -F -oA nmapScan --stylesheet nmap-bootstrap.xsl 10.0.2.0/24`

##### Detect NetBIOS (PC Name) with nmap
`nmap -sV --script=rdp-vuln-ms12-020 -p 3389 10.0.0.0'

##### nmap Eternal Blue
`nmap -Pn -p445 --script=smb-vuln-ms17-010 192.168.1.0/24 -oN eternalblue-results.txt`

##### Metasploit Bluekeep scan
```
msfconsole
search bluekeep
use auxiliary/scanner/rdp/cve_2019_0708_bluekeep
set RHOSTS 192.168.1.0/24
show options
run
```


