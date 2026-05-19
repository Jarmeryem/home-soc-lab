# Lab Architecture

## Topology
Isolated internal network (VirtualBox) — 192.168.10.0/24

| VM | OS | IP | Role |
|---|---|---|---|
| VM1 | Kali Linux 2024 | 192.168.10.10 | Attacker + Suricata IDS |
| VM2 | Ubuntu Server 22.04 | 192.168.10.20 | Vulnerable target |
| VM3 | Ubuntu Server 22.04 | 192.168.10.30 | ELK Stack (SIEM) |

## Network Interfaces
Each VM has two interfaces:
- **eth0** : NAT (Internet access for updates)
- **eth1** : Internal network SOC-NET (attack traffic)

## Resources
| VM | RAM | CPU | Storage |
|---|---|---|---|
| Kali | 3 GB | 2 vCPU | 40 GB |
| Target | 1 GB | 1 vCPU | 20 GB |
| ELK | 6 GB | 2 vCPU | 60 GB |

## Design Choices
- Static IPs ensure stable log collection even after reboot
- Suricata runs on Kali on the same interface as attacks (eth1)
  for direct traffic capture
- Flat network (no VLAN) — intentional for lab simplicity,
  documented as a weakness in incident reports
