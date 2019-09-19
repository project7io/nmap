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

### Host discovery via smb
`nmap -p 445 --script smb-os-discovery 192.168.1.0/24`


## Formatting
`wget https://raw.githubusercontent.com/honze-net/nmap-bootstrap-xsl/master/nmap-bootstrap.xsl`

`nmap -sS -T4 -A -sC -oA nmapScan --stylesheet nmap-bootstrap.xsl 192.168.0.1`
