# Suricata Custom Rules

Custom rules written for this lab, stored in `/etc/suricata/rules/local.rules`.

| SID | Description | Triggered by |
|---|---|---|
| 1000001 | ICMP Ping detection | Nmap -sn |
| 1000002 | SYN scan detection | Nmap -sS, -A |
| 1000003 | NULL scan detection | Nmap -A |
| 1000004 | SSH brute force | Hydra SSH attack |
| 1000005 | XMAS scan detection | Nmap -A |

Public Emerging Threats rules also used (no modification needed):
- SID 2027865 : ET EXPLOIT Metasploit Meterpreter PHP Stager
- SID 2002911 : ET WEB_SERVER DVWA File Upload Attempt
- SID 2012887 : ET INFO HTTP POST contains pass= in cleartext
