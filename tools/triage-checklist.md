# Triage Checklist

- [ ] Download official firmware; record SHA-256 in `firmware/firmware.sha256`
- [ ] Extract with binwalk (`-eM`) into `/extracted`
- [ ] Generate SBOM (`syft`) → `/sbom/sbom.json` (CycloneDX)
- [ ] Run vulnerability scan (`grype`) → `/reports/vuln-report.json`
- [ ] Stand up emulation (FirmAE/Firmadyne) → document in `/emulation/setup.md`
- [ ] Capture traffic during adversarial tests → `/emulation/pcap/*.pcap`
- [ ] Document findings → `/reports/triage-notes.md`
- [ ] Propose mitigations → `/hardening/mitigations.md`
