# 🛰️ TP-Link Router Firmware Security Project

## 📌 Project Summary
This project documents a full hardware + firmware security triage of the TP-Link TL-WR841N router.

> ⚠️ Research use only. Do not test on production networks. Keep analysis in an isolated lab/emulator.

---

## ⚙️ Scope
- Hardware exploration (UART, flash)
- Firmware dumping & validation
- Static firmware analysis (binwalk, strings, Ghidra)
- Credential recovery & hash cracking
- Network scanning & CVE research

---

## 🔬 Quickstart
- [UART Cheatsheet](tools/uart-cheatsheet.md)
- [Firmware Triage Checklist](tools/firmware-triage-checklist.md)
- [Hash Cracking Guidance](tools/hash-cracking-guidance.md)
- [Full Triage Report](reports/tl-wr841n-triage.md)

---

## ✈️ Aerospace/Defense Mapping
- **Supply-chain assurance:** SBOM + VEX triage (CISA-aligned) informs acceptance decisions.
- **Assurance & certification:** Supports DO-326A/ED-202A activities; ties to NIST SP 800-160 cyber resiliency.
- **Adversarial/chaotic tests:** De-risk before real hardware-in-the-loop; mirrors methods used for avionics comms.

---

## 📂 Repository Layout
```
IoT-Router-Triage/
├─ firmware/                 # raw flash dumps (wr841n_1.bin, wr841n_2.bin)
├─ extracted/                # binwalk extracted filesystems
├─ reports/
│   └─ tl-wr841n-triage.md   # polished, narrative walk-through
├─ tools/
│   ├─ uart-cheatsheet.md
│   ├─ firmware-triage-checklist.md
│   └─ hash-cracking-guidance.md
└─ README.md
```

---

## ⚠️ Safety & Ethics
- Research/education only; **no production testing**.
- Keep all work on **isolated hosts/emulation** you control.
- Respect licenses and legal constraints for firmware use.

---

## 📖 References
- TCM Security Beginner's Guide to IoT and Hardware Hacking
- NIST SP 800-160 Vol. 2 — *Developing Cyber Resilient Systems*
- CISA — *SBOM Myths vs. Facts*
- DO-326A / ED-202A — *Airworthiness Security Process*
- (Add vendor advisory links and CVEs you find during analysis)








