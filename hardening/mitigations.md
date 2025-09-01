# Mitigations

## Configuration hardening
- Disable WAN-side admin and UPnP by default.
- Enforce HTTPS-only admin, HSTS, and strong CSRF tokens.
- Restrict services to LAN; add firewall rules and sane defaults.

## Patch strategy
- Update or replace EoL components (BusyBox, web server, dnsmasq).
- Track vendor advisories and map SBOM components to CVEs (VEX triage).
