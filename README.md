#### nmap
 Project7 nmap notes -- Best viewed as a GitHub page  https://project7io.github.io/nmap/

#### Install NSE scripts to detect vulnerabilities

- Change directory to nmap scripts folder
'cd /usr/share/nmap/scripts/'

- Install/clone scripts
'git clone https://github.com/vulnersCom/nmap-vulners.git && git clone https://github.com/scipag/vulscan.git'

- Update vulscan database
'cd vulscan/utilities/updater/ && chmod +x updateFiles.sh && ./updateFiles.sh'

- Scan with nmap-vunlers
'nmap --script nmap-vulners -sV -p# ###.###.###.###'

- Scan with vulscan 
`nmap --script vulscan -sV -p# ###.###.###.###`

--Combine both scripts to one scan and scan ALL ports
`nmap --script nmap-vulners,vulscan --script-args vulscandb=scipvuldb.csv -sV -p- ###.###.###.###`

--Host discovery via smb
nmap -p 445 --script smb-os-discovery 192.168.1.0/24
