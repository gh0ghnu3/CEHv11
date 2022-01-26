
# nmap

nmap is the de facto tool for scanning, enumeration, version detection, and lots of other things. So be patient learning different aspects of using it. 

## Command Snippets
You can always use nmap help to find out about what different switches do, simply use --help

```
nmap --help
```
In the following sections, there some examples regarding defferent aspects of using nmap.

- **Ping Scans**
These two lines of commands do the same thing! The default behavior of nmap when you use **ping sweep scan** is sending a SYN packet to port 443, an ACK packet to the port 80, an ICMP echo (PE), and and ICMP timestamp (PP) to the target you specified.
```
nmap -PS443 -PA80 -PE -PP <Target IP> 
nmap -sn <target IP>
```
```
nmap -sn -PR --spoof-mac <mac address> <target>
```
You should also bear in mind that using nmap as a privileged user may have different results versus when you're using it as a normal user. Wandering why? Because some of the packet creation mechanisms in OS are available only for the privileged users.
- **TCP and UDP scans**
```
nmap --send-ip -sn -PS21,22,23,25,80,445,443,3389,8080 -PA80,443,8080 - PO1,2,4,6 -PU631,161,137,123 192.168.1.1/24
```

- **Scripts**
```
nmap --script http-headers,http-title scanme.nmap.org

nmap -sV --script vuln <target>

nmap --script http-enum -sV <target>
```
