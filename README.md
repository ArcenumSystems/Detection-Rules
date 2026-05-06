<div align="center">

  <img src="https://img.shields.io/github/stars/ArcenumSystems/Detection-Rules?style=for-the-badge&color=yellow&logo=github" />
  <img src="https://img.shields.io/github/forks/ArcenumSystems/Detection-Rules?style=for-the-badge&color=blue&logo=github" />
  <img src="https://img.shields.io/github/issues/ArcenumSystems/Detection-Rules?style=for-the-badge&color=red&logo=github" />
  <img src="https://img.shields.io/github/last-commit/ArcenumSystems/Detection-Rules?style=for-the-badge&color=green&logo=github" />

  <br><br>

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
  <img src="https://img.shields.io/badge/Rules-60%2B-ff4444?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Threat_Actors-8-6366f1?style=for-the-badge" />

</div>

<br>

<div align="center">

# Arcenum Systems — Universal SIEM Detection Rules

**If this project helped you, please ⭐ star the repo — it helps others find it!**

</div>

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
| Lateral Movement | DCOM (FIN7) | Lazarus kill chain |
| Collection | Clipboard hijack (Lazarus) | — |

---

## Troubleshooting

Every rule contains a `TROUBLESHOOTING` section. If a rule is not firing:
1. Follow the in-rule troubleshooting steps first
2. Open an issue at [github.com/ArcenumSystems/Detection-Rules](https://github.com/ArcenumSystems/Detection-Rules)
3. Contact: [github.com/PradhyumnaGhogare](https://github.com/PradhyumnaGhogare)

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

- **GitHub:** [github.com/PradhyumnaGhogare](https://github.com/PradhyumnaGhogare)
- **Organization:** [github.com/ArcenumSystems](https://github.com/ArcenumSystems)

---

*Engineered for adversaries who think no one is watching.*  
**— Pradhyumna Ghogare, Arcenum Systems © 2024**
