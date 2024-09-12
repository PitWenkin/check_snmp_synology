# Check SNMP Synology
Nagios/Icinga script to check Synology via SNMP

It's based on version 2.5 check_snmp_synology for nagios by Nicolas Ordonez
https://exchange.nagios.org/directory/Plugins/Network-and-Systems-Management/Others/Synology-status/details

Due to timeouts and none of the solutions proposed in the comments of the initial script I rewrote the first SNMPWalk to a something similar to that used by version 1.1 of the same script.
Added checks to USB-storage mounting an disk-usage

# Usage

./check_snmp_synology [OPTION] -u [user] -p [pass] -h [hostname] 

# Options:
```
  -u [snmp username] Username for SNMPv3 
  -p [snmp password] Password for SNMPv3 

  -2 [community name] Use SNMPv2 (no need user/password) & define community name (ex: public) 

  -h [hostname or IP](:port)	Hostname or IP. You can also define a different port 

  -W [warning temp] Warning temperature (for disks & synology) (default 50) 
  -C [critical temp] Critical temperature (for disks & synology) (default 60) 

  -w [warning %] Warning storage usage percentage (default 80) 
  -c [critical %] Critical storage usage percentage (default 95) 

  -b [number of USB slot] Check USB-storage

  -i Ignore DSM updates 
  -U Show informations about the connected UPS (only information, no control) 
  -v Verbose - print all informations about your Synology 
```

# Examples:
```
  ./check_snmp_synology -u admin -p 1234 -h nas.intranet 
  ./check_snmp_synology -u admin -p 1234 -h nas.intranet -v 
  ./check_snmp_synology -2 public -h nas.intranet 
  ./check_snmp_synology -2 public -h nas.intranet -b 2
  ./check_snmp_synology -2 public -h nas.intranet:10161 
```
