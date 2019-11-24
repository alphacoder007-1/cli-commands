Netoworking Commands for prgrammers
====================================

### Display all TCP/IP network config values

    ipconfig
    ipconfig /all
    ipconfig /all |more

### nslookup - Name Server lookup

    nslookup microsfot.com

    nslookup www.google.com


### tracert - Determine the route packet takes from source to destination

    tracert microsoft.com

    tracert amazon.com

### pathping - combines ping and tracert functionalities

    pathping microsoft.com

### route PRINT - to print route table

    route PRINT

## Port Connectivity

### telnet - allows you to connect to remote computer , telnet is good if you know the port

    telnet google.com 80
    telnet google.com 81
    telnet google.com 1433 

### nmap - network mapper used for discovering hosts and services on a compuer network

    nmap google.com
    nmap -v microsoft.com

### netstat -ano - to determine which ports and process are open in our machine

    netstat -ano




