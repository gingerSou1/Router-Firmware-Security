# Emulation Setup (FirmAE / Firmadyne)

> Use either framework; steps vary slightly by host OS. Record the exact steps you follow here so results are reproducible.

## Example outline (FirmAE)
1. Clone FirmAE and install prerequisites.
2. Place your TP-Link firmware `.bin` into the expected images directory.
3. Run analysis script to build a QEMU runnable image.
4. Note the emulated IP/ports that FirmAE assigns.
5. Verify services (HTTP admin UI, UPnP, etc.) with `curl/nmap`.
6. Capture traffic during tests: `sudo tcpdump -i any -w emulation/pcap/emu-session.pcap`.

## Tips
- Some firmwares need `binwalk -Me` first; copy the rootfs into FirmAE’s expected layout.
- If the web UI doesn’t come up, check init scripts in `/etc/rc*`, `/etc/init.d/`, and `inetd` configs.
