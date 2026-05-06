# Arcenum Systems — Universal SIEM Detection Rules

> **Author:** Pradhyumna Ghogare
> **Copyright:** © 2024 Pradhyumna Ghogare / Arcenum Systems
> **Project:** Arcenum Systems Universal Threat Detection Engine
> **Version:** 3.0.0
> **MITRE ATT&CK:** v14.0
> **GitHub:** [github.com/ArcenumSystems](https://github.com/ArcenumSystems) | [github.com/PradhyumnaGhogare](https://github.com/PradhyumnaGhogare)

---

> ⚠️ **PROPRIETARY DETECTION LOGIC**
> All detection patterns, correlation logic, APT fingerprints, and MITRE mappings
> are original research by **Pradhyumna Ghogare / Arcenum Systems**.
> Do not redistribute without attribution.

---

## Overview

Production-grade, real-world APT-based detection rules for **all 6 major SIEM platforms**.
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
│   ├── advanced/          # Single-event SPL detections (10 rules)
│   └── correlation/       # Multi-stage kill chain correlations (5 rules)
├── sentinel/
│   ├── advanced/          # KQL analytics rules (8 rules)
│   └── correlation/       # Multi-stage KQL correlations (3 rules)
├── crowdstrike/
│   ├── advanced/          # CrowdStrike FQL detections (5 rules)
│   └── correlation/       # FQL kill chain correlations (2 rules)
├── elastic/
│   ├── advanced/          # EQL detection rules (5 rules)
│   └── correlation/       # EQL sequence correlations (1 rule)
├── sigma/
│   ├── advanced/          # Universal Sigma rules (7 rules)
│   └── correlation/       # Sigma correlation rules (1 rule)
└── chronicle/
    ├── advanced/          # YARA-L single detections (4 rules)
    └── correlation/       # YARA-L multi-event correlations (2 rules)
```

---

## Threat Actor Coverage

| Actor | Origin | TTPs Covered | Platforms |
|-------|--------|--------------|-----------|
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

| Category | Rules | MITRE |
|----------|-------|-------|
| Credential Access | LSASS, DCSync, Kerberoasting, Golden Ticket, Golden SAML | T1003, T1558, T1606 |
| Defense Evasion | AMSI bypass, ETW patch, GuardDuty disable | T1562 |
| Persistence | WMI subscriptions (APT41) | T1546.003 |
| Ransomware | Shadow copy, rapid encryption, full kill chain | T1486, T1490 |
| Cloud | AWS GuardDuty, Golden SAML, IMDS SSRF | T1562.008, T1606 |
| Network | DNS tunneling, C2 beaconing, brute force chain | T1071, T1110 |
| Identity | MFA fatigue, SIM swap | T1621, T1078 |
| Container | cgroup escape, Docker socket abuse | T1611 |
| Lateral Movement | DCOM (FIN7), WMI exec | T1021.003 |
| Collection | Clipboard hijack (Lazarus) | T1414 |
| Kill Chains | APT29, APT41, Lazarus, Ransomware, Brute-force-to-C2 | Multiple |

---

## Troubleshooting

Every rule contains a `TROUBLESHOOTING` section covering:
1. Required audit policies / GPO settings
2. Data source verification commands
3. Threshold tuning guidance
4. False positive management
5. Contact info for unresolved issues

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
Or: Kibana Dev Tools → POST kbn:/api/detection_engine/rules
```

### Sigma (Universal — compile to any SIEM)
```bash
pip install sigma-cli pySigma-backend-splunk pySigma-backend-microsoft365defender
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
