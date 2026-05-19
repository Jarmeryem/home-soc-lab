# Home SOC Lab — IDS/SIEM with Suricata & ELK Stack

> Final year project (PFE) — Master Réseaux et Systèmes Informatiques  
> Université Hassan 1er — FST Settat — 2025/2026  
> Supervised by: Pr. Chaimae Azroumahli

## Overview
Design and deployment of a virtualized SOC (Security Operations Center)
to detect, analyze and visualize network intrusions in real time.

**Stack:** Suricata IDS · Elasticsearch · Logstash · Kibana · VirtualBox · Kali Linux

## Architecture
Three VMs on an isolated internal network (192.168.10.0/24):

- **VM1 Kali Linux** (192.168.10.10) — Attacker + Suricata IDS
- **VM2 Ubuntu Server** (192.168.10.20) — Vulnerable target
- **VM3 ELK Stack** (192.168.10.30) — SIEM (Elasticsearch + Logstash + Kibana)

[Full architecture details →](architecture/README.md)

## Attacks Simulated

| Attack | Tool | Alerts detected | Phase |
|---|---|---|---|
| Network Reconnaissance | Nmap | 18 | Reconnaissance |
| SSH + HTTP Brute Force | Hydra v9.5 | 34 | Exploitation |
| Web Exploit + Reverse Shell | Metasploit | 97 | Exploitation + Installation |

## Detection Pipeline

Kali (attack) → Suricata IDS → EVE-JSON logs→ Logstash → Elasticsearch → Kibana dashboard

## Key Results
- Real-time detection of all 3 attack types
- Custom Suricata rules (SID 1000001–1000005) for Nmap/Hydra
- Kibana SOC dashboard with KPI, timeline, top signatures, top IPs
- Full incident reports with IoC tables and remediation recommendations

## Repository Structure
- [architecture/](architecture/) — Network topology and addressing plan
- [incident-reports/](incident-reports/) — 3 SOC incident reports (PDF)
- [suricata-rules/](suricata-rules/) — Custom detection rules
- [network-config/](network-config/) — VM network configuration files
- [elk-config/](elk-config/) — Logstash pipeline configuration
