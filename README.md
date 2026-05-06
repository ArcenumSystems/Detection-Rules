<div align="center">
  
  <!-- Platform & Language Badges -->
  <img src="https://img.shields.io/badge/Splunk-SPL-000000?style=for-the-badge&logo=splunk&logoColor=white" />
  <img src="https://img.shields.io/badge/Sentinel-KQL-0078D4?style=for-the-badge&logo=microsoft&logoColor=white" />
  <img src="https://img.shields.io/badge/CrowdStrike-FQL-CC0000?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Chronicle-YARA--L-4285F4?style=for-the-badge&logo=google&logoColor=white" />
  <img src="https://img.shields.io/badge/Elastic-EQL-005571?style=for-the-badge&logo=elasticsearch&logoColor=white" />
  <img src="https://img.shields.io/badge/Sigma-Universal-005E9C?style=for-the-badge" />
  

  <br><br>

  <!-- Metrics & Versioning Badges -->
  <img src="https://img.shields.io/badge/MITRE_ATT%26CK-v14.0-e8382f?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Architecture-Advanced_%26_Correlation-22c55e?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Coverage-6_Platforms-a855f7?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Version-3.0.0-f59e0b?style=for-the-badge" />

</div>

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
Each rule includes:
- `WHY THIS FIRES` — so your SOC knows exactly who is in the environment
- `TROUBLESHOOTING` — step-by-step fix if the rule is not firing
- `CONTACT` — where to reach for IR support

---

## Repository Structure

```
Detection-Rules/
├── splunk/
│   ├── advanced/          # Single-event SPL detections (18 rules)
│   └── correlation/       # Multi-stage kill chain correlations (5 rules)
├── sentinel/
│   ├── advanced/          # KQL analytics rules (8 rules)
│   └── correlation/       # Multi-stage KQL correlations (3 rules)
├── crowdstrike/
│   ├── advanced/          # CrowdStrike FQL detections (5 rules)
│   └── correlation/       # FQL kill chain correlations (2 rules)
├── chronicle/
│   ├── advanced/          # YARA-L single detections (4 rules)
│   └── correlation/       # YARA-L multi-event correlations (2 rules)
├── elastic/
│   ├── advanced/          # EQL detection rules (5 rules)
│   └── correlation/       # EQL sequence correlations (1 rule)
└── sigma/
    ├── advanced/          # Universal Sigma rules (7 rules)
    └── correlation/       # Sigma correlation rules (1 rule)
```

---

## Threat Actor Coverage

| Actor | Origin | TTPs Covered | Platforms |
|---|---|---|---|
| **APT29 (Cozy Bear)** | Russia | SUNBURST, DLL sideload, Golden SAML, DCSync, AMSI bypass | All 6 |
| **APT41 (Winnti/Barium)** | China | WMI persistence, supply chain, DCOM, kill chain | All 6 |
| **Lazarus Group** | North Korea | Clipboard hijack, crypto theft, Docker miner, kill chain | All 6 |
| **BlackCat/ALPHV** | Unknown | Full ransomware kill chain | All 6 |
| **Scattered Spider** | English | MFA fatigue, SIM swap, cloud attacks | All 6 |
| **LockBit 3.0** | Unknown | Rapid encryption, pre-ransomware recon | All 6 |
| **Volt Typhoon** | China | LOTL recon, IMDS SSRF, critical infra | All 6 |
| **FIN7 (Carbanak)** | Eastern Europe | DCOM lateral movement, DNS tunneling | All 6 |

---

## Rule Categories

| Category | Advanced | Correlation |
|---|---|---|
| Credential Access | LSASS, DCSync, Kerberoasting, Golden Ticket, Golden SAML | APT29 kill chain |
| Defense Evasion | AMSI bypass, ETW patch, GuardDuty disable | — |
| Persistence | WMI subscriptions (APT41) | APT41 kill chain |
| Ransomware | Shadow copy deletion, rapid encryption | Full ransomware kill chain |
| Cloud | AWS GuardDuty, Golden SAML | — |
| Network | DNS tunneling, C2 beaconing | Brute force → C2 |
| Identity | MFA fatigue, SIM swap | — |
| Container | cgroup escape, Docker socket abuse | — |
| Lateral Movement | DCOM (FIN7), WMI exec | Lazarus kill chain |
| Collection | Clipboard hijack (Lazarus) | — |

---

## Troubleshooting

Every rule contains a `TROUBLESHOOTING` section covering:
1. Required audit policies / GPO settings
2. Data source verification commands
3. Threshold tuning guidance
4. False positive management

**If a rule is still not firing after following troubleshooting steps:**  
→ Open an issue at [github.com/ArcenumSystems/Detection-Rules](https://github.com/ArcenumSystems/Detection-Rules)  
→ Contact: [github.com/PradhyumnaGhogare](https://github.com/PradhyumnaGhogare)

---

## Deployment

### Splunk
```
Settings → Searches, Reports and Alerts → New Search → Paste .spl content
```

### Microsoft Sentinel
```
Analytics → Create → Scheduled query rule → Paste .kql content
```

### CrowdStrike Falcon
```
Investigate → Event Search → Paste .fql query
```

### Google Chronicle
```
Detection Engine → Rules → New Rule → Paste .yaral content
```

### Elastic SIEM
```
Security → Rules → Import rules → Upload .toml file
```

### Sigma (Universal — compile to any SIEM)
```bash
pip install sigma-cli
sigma convert -t splunk  sigma/advanced/lsass_access.yml
sigma convert -t sentinel sigma/advanced/lsass_access.yml
sigma convert -t elasticsearch sigma/advanced/lsass_access.yml
```

---

## About

Built by **Pradhyumna Ghogare** as part of **Arcenum Systems** — an independent  
cybersecurity R&D initiative delivering enterprise-grade detection engineering.

- **GitHub:** [github.com/PradhyumnaGhogare](https://github.com/PradhyumnaGhogare)
- **Organization:** [github.com/ArcenumSystems](https://github.com/ArcenumSystems)

---

*Engineered for adversaries who think no one is watching.*  
**— Pradhyumna Ghogare, Arcenum Systems © 2024**
