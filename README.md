#### nmap
 Project7 nmap notes -- Best viewed as a Gitpage  https://project7io.github.io/nmap/

#### Install NSE scripts to detect vulnerabilities

- Change directory to nmap scripts folder
##### cd /usr/share/nmap/scripts/

- Install/clone scripts
##### git clone https://github.com/vulnersCom/nmap-vulners.git && git clone https://github.com/scipag/vulscan.git 

- Update vulscan database
##### cd vulscan/utilities/updater/ && chmod +x updateFiles.sh && ./updateFiles.sh
##### 
