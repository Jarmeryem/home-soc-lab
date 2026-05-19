# ELK Stack Configuration

## Pipeline
Suricata generates EVE-JSON logs → Logstash reads and parses
→ sends to Elasticsearch → visualized in Kibana

## Logstash
Config file: `/etc/logstash/conf.d/suricata.conf`
See: `logstash-suricata.conf`

## Elasticsearch
- Index pattern: `suricata-*`
- Running on: 192.168.10.30:9200

## Kibana
- Running on: 192.168.10.30:5601
- Dashboard: SOC - Suricata Overview
- Visualizations: KPI total alerts, timeline, top signatures,
  top source IPs, attack types, top ports
