# Commands Cheatsheet

## Hash & extract
sha256sum firmware/firmware.bin > firmware/firmware.sha256
binwalk -eM firmware/firmware.bin -C extracted

## SBOM & vuln scan
syft dir:./extracted -o cyclonedx-json > sbom/sbom.json
grype dir:./extracted -o json > reports/vuln-report.json

## Emulation capture
sudo tcpdump -i any -w emulation/pcap/session.pcap

## Recon / fuzz examples
ffuf -u http://<emu_ip>FUZZ -w /usr/share/seclists/Discovery/Web-Content/common.txt -mc all -fs 0
