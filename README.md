### nmap
 Project7 nmap notes -- Best viewed as a GitHub page  https://project7io.github.io/nmap/

### Install NSE scripts to detect vulnerabilities

`cd /usr/share/nmap/scripts/ && git clone https://github.com/vulnersCom/nmap-vulners.git && git clone https://github.com/scipag/vulscan.git && cd /usr/share/nmap/scripts/vulscan/utilities/updater && chmod +x updateFiles.sh && ./updateFiles.sh`

Scan with nmap-vunlers
`nmap --script nmap-vulners -sV -p# ###.###.###.###`

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

Then XML to HTML
`xsltproc -o nmapScan.html nmap-bootstrap.xsl nmapScan.xml`
