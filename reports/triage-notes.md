# Triage Notes

## Device & Firmware
- Vendor/Model:
- Firmware filename:
- Version / Build date:
- Hash (SHA-256): `cat firmware/firmware.sha256`

## Components Observed (partial)
- BusyBox:
- libc (uClibc/musl/glibc):
- web server (uhttpd/lighttpd/nginx):
- ssh/telnet:
- dnsmasq/udhcpd:
- kernel version:

## Vulnerability Highlights
- (example) dnsmasq CVE-2020-25681 — observed version X.Y.Z
- (example) lighttpd CVE-XXXX-YYYY — observed version …

## Emulation Notes
- Emulator used (FirmAE/Firmadyne):
- Emulated IP / interfaces:
- Services reachable:
- Known quirks:

## Adversarial Tests
- Web UI discovery:
- Parameter fuzz cases:
- UPnP/SSDP behaviors:
- DHCP option tests:
- Observed crashes/hangs/logs:

## Mitigations (candidate hardening)
- Disable WAN admin / UPnP by default
- Enforce HTTPS-only admin, strong CSRF
- Update/replace EoL packages
