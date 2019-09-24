### nmap
 Project7 nmap notes -- Best viewed as a GitHub page  https://project7io.github.io/nmap/

### Install NSE scripts to detect vulnerabilities

`cd /usr/share/nmap/scripts/ && git clone https://github.com/vulnersCom/nmap-vulners.git && git clone https://github.com/scipag/vulscan.git && cd /usr/share/nmap/scripts/vulscan/utilities/updater && chmod +x updateFiles.sh && ./updateFiles.sh`

Scan with nmap-vunlers
`nmap --script nmap-vulners -sV -p# ###.###.###.###`

#### Example results:
```Nmap scan report for 10.0.2.7/r
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
MAC Address: 08:00:27:10:B8:D0 (Oracle VirtualBox virtual NIC)```


Scan with vulscan 
`nmap --script vulscan -sV -p# ###.###.###.###`

### Combine both scripts to one scan and scan ALL ports
`nmap --script nmap-vulners,vulscan --script-args vulscandb=scipvuldb.csv -sV -p- ###.###.###.###`

### Eternal Blue
`nmap -Pn -p445 --script=smb-vuln-ms17-010 192.168.1.0/24 -oN eternalblue-results.txt`

### Bluekeep scan
`msfconsole`
`search bluekeep`
`use auxiliary/scanner/rdp/cve_2019_0708_bluekeep`
`set RHOSTS 192.168.1.0/24`
`show options`
`run`

### Formatting
`wget https://raw.githubusercontent.com/honze-net/nmap-bootstrap-xsl/master/nmap-bootstrap.xsl`

`nmap -sS -T4 -A -sC -oA nmapScan --stylesheet nmap-bootstrap.xsl 192.168.0.1`

- Then XML to HTML
`xsltproc -o nmapScan.html nmap-bootstrap.xsl nmapScan.xml`
