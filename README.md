# 🛰️ TP-Link Router Firmware Security Project

## 📌 Project Summary
This repository demonstrates a **firmware security triage workflow** for a TP-Link router image. It focuses on **supply-chain assurance**, **SBOM/VEX-driven vulnerability analysis**, and **safe emulation with adversarial tests** — aligning with aerospace/defense assurance practices.

**Key outcomes:**
- Extract firmware and identify components
- Generate **SBOM (CycloneDX)** and perform **vulnerability scans**
- **Emulate** firmware safely in QEMU (FirmAE/Firmadyne)
- Run **adversarial tests** (web UI, UPnP, DHCP) in isolation
- Document **findings and mitigations**

> ⚠️ Research use only. Do not test on production networks. Keep analysis in an isolated lab/emulator.

---

## ⚙️ Tools
- `binwalk` – firmware extraction
- `syft` – SBOM generation (CycloneDX)
- `grype` – vulnerability scanning (CVE/NVD)
- `firmAE` or `Firmadyne` – QEMU-based emulation
- `tcpdump` / `tshark` – capture
- `ffuf` / `gobuster` / `curl` – adversarial HTTP tests

---

## 🔬 Workflow Overview
```
1) Acquire stock TP-Link firmware (.bin) → put in /firmware and record hash
2) Extract with binwalk → write output to /extracted
3) Generate SBOM with syft → save to /sbom (CycloneDX JSON)
4) Scan vulnerabilities with grype → save to /reports
5) Emulate in FirmAE/Firmadyne → keep notes in /emulation/setup.md
6) Run adversarial tests (web UI, UPnP, DHCP) → store pcaps in /emulation/pcap
7) Document findings + mitigations → /reports/triage-notes.md, /hardening/mitigations.md
```

---

## 🧪 Quick Commands (cheatsheet)

### Hash & extract
```bash
cd firmware
sha256sum firmware.bin > firmware.sha256

# back to repo root
binwalk -eM firmware/firmware.bin -C extracted
```

### SBOM & vulnerability scan
```bash
# SBOM (CycloneDX JSON)
syft dir:./extracted -o cyclonedx-json > sbom/sbom.json

# Vulnerability scan
grype dir:./extracted -o json > reports/vuln-report.json
```

### Emulation (example FirmAE workflow)
```bash
# Follow /emulation/setup.md for your host; example outline:
# 1) clone FirmAE
# 2) place firmware in FirmAE images folder
# 3) run analysis scripts; note assigned tap IP/ports
# 4) browse emulated web UI; confirm services (http/https/ssh/telnet)
```

### Adversarial HTTP tests (examples)
```bash
# Directory/content discovery
ffuf -u http://<emu_ip>FUZZ -w /usr/share/seclists/Discovery/Web-Content/common.txt -mc all -fs 0

# Simple fuzz of a CGI endpoint (parameters vary per firmware)
ffuf -u 'http://<emu_ip>/cgi-bin/login?user=FUZZ&pass=FUZZ' -w /usr/share/seclists/Passwords/Common-Credentials/10-million-password-list-top-1000.txt -mr 'error|invalid|success'

# UPnP / SSDP probe (on host)
echo -ne 'M-SEARCH * HTTP/1.1
HOST:239.255.255.250:1900
MAN:"ssdp:discover"
MX:2
ST:ssdp:all

' | nc -u -w 2 239.255.255.250 1900
```

---

## ✈️ Aerospace/Defense Mapping
- **Supply-chain assurance:** SBOM + VEX triage (CISA-aligned) informs acceptance decisions.
- **Assurance & certification:** Supports DO-326A/ED-202A activities; ties to NIST SP 800-160 cyber resiliency.
- **Adversarial/chaotic tests:** De-risk before real hardware-in-the-loop; mirrors methods used for avionics comms.

---

## 📂 Repository Layout
```
tp-link-firmware-security/
├─ firmware/            # stock .bin + firmware.sha256
├─ extracted/           # binwalk output
├─ sbom/                # SBOM (CycloneDX JSON)
├─ reports/
│  ├─ vuln-report.json
│  └─ triage-notes.md
├─ emulation/
│  ├─ setup.md
│  └─ pcap/
├─ hardening/
│  ├─ mitigations.md
│  └─ openwrt-configs/
└─ tools/
   ├─ triage-checklist.md
   └─ commands-cheatsheet.md
```

---

## ⚠️ Safety & Ethics
- Research/education only; **no production testing**.
- Keep all work on **isolated hosts/emulation** you control.
- Respect licenses and legal constraints for firmware use.

---

## 📖 References
- NIST SP 800-160 Vol. 2 — *Developing Cyber Resilient Systems*
- CISA — *SBOM Myths vs. Facts*
- DO-326A / ED-202A — *Airworthiness Security Process*
- (Add vendor advisory links and CVEs you find during analysis)
