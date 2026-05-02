# Arcenum Systems — Universal SIEM Detection Rules

> **Author:** Pradhyumna Ghogare  
> **Copyright:** © 2024 Pradhyumna Ghogare / Arcenum Systems  
> **Project:** Arcenum Systems Universal Threat Detection Engine  
> **Version:** 3.0.0  
> **MITRE ATT&CK:** v14.0  

---

> ⚠️ **PROPRIETARY DETECTION LOGIC**  
> All detection patterns, correlation logic, APT fingerprints, and MITRE mappings  
> are original research by **Pradhyumna Ghogare / Arcenum Systems**.  
> Do not redistribute without attribution.

---

## Overview

Production-grade, real-world APT-based detection rules for all major SIEM platforms.  
Every rule is based on **documented threat actor behavior from actual incidents**.  
Each rule includes `WHY THIS FIRES` — so your SOC knows exactly who is in the environment.

---

## Repository Structure

```
arcenum-systems-detection-rules/
├── splunk/
│   ├── advanced/          # Single-event SPL detections
│   └── correlation/       # Multi-stage kill chain correlations
├── sentinel/
│   ├── advanced/          # KQL analytics rules
│   └── correlation/       # Multi-stage KQL correlations
├── crowdstrike/
│   ├── advanced/          # CrowdStrike FQL detections
│   └── correlation/       # FQL kill chain correlations
├── chronicle/
│   ├── advanced/          # YARA-L single detections
│   └── correlation/       # YARA-L multi-event correlations
├── elastic/
│   ├── advanced/          # EQL detection rules
│   └── correlation/       # EQL sequence correlations
└── sigma/
    ├── advanced/          # Universal Sigma rules
    └── correlation/       # Sigma correlation rules
```

---

## Threat Actor Coverage

| Actor | Origin | TTPs Covered |
|---|---|---|
| **APT29 (Cozy Bear)** | Russia | SUNBURST, DLL sideload, Golden SAML, DCSync |
| **APT41** | China | WMI persistence, supply chain, DCOM |
| **Lazarus Group** | North Korea | Clipboard hijack, crypto theft, Docker miner |
| **BlackCat/ALPHV** | Unknown | Full ransomware kill chain |
| **Scattered Spider** | English | MFA fatigue, SIM swap, cloud attacks |
| **LockBit 3.0** | Unknown | Rapid encryption, pre-ransomware recon |
| **Volt Typhoon** | China | LOTL recon, IMDS SSRF, critical infra |
| **FIN7** | Eastern Europe | DCOM lateral movement, DNS tunneling |

---

## Rule Categories

| Category | Advanced | Correlation |
|---|---|---|
| Credential Access | LSASS, DCSync, Kerberoasting, Golden Ticket | APT29 kill chain |
| Defense Evasion | AMSI bypass, ETW patch, GuardDuty disable | — |
| Ransomware | Shadow copy deletion | Full ransomware kill chain |
| Cloud | AWS GuardDuty, Golden SAML, IMDS SSRF | — |
| Network | DNS tunneling, C2 beaconing | Brute force → C2 |
| Identity | MFA fatigue, SIM swap | — |
| Container | cgroup escape, Docker socket abuse | — |

---

## Deployment

### Splunk
```
Settings → Searches, Reports and Alerts → Import .spl file
```

### Microsoft Sentinel
```
Analytics → Create → Import rule → Upload .kql file
```

### CrowdStrike Falcon
```
Investigate → Event Search → Paste .fql query
```

### Google Chronicle
```
Detection Engine → Rules → New Rule → Import .yaral file
```

### Elastic SIEM
```
Security → Rules → Import rules → Upload .toml file
```

### Sigma (Universal)
```bash
pip install sigmatools
sigmac -t splunk sigma/advanced/lsass_access.yml
sigmac -t sentinel sigma/advanced/lsass_access.yml
```

---

## About

Built by **Pradhyumna Ghogare** as part of **Arcenum Systems** — an independent  
cybersecurity R&D initiative delivering enterprise-grade detection engineering.

- **Website:** [arcenum-systems.vercel.app](https://arcenum-systems.vercel.app)
- **GitHub:** [github.com/PradhyumnaGhogare](https://github.com/PradhyumnaGhogare)
- **Organization:** [github.com/ArcenumSystems](https://github.com/ArcenumSystems)

---

*Engineered for adversaries who think no one is watching.*  
**— Pradhyumna Ghogare, Arcenum Systems © 2024**
