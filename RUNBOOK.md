# Raspberry Pi 5 — Home Lab Runbook

## System Details

| Field    | Value                                      |
|----------|--------------------------------------------|
| Device   | Raspberry Pi 5 8GB                         |
| OS       | Raspberry Pi OS Lite 64-bit (Debian Trixie)|

## OS Installation

1. Download the Raspberry Pi Imager from https://www.raspberrypi.com/software/
2. Download Raspberry Pi OS Lite (64-bit) from https://www.raspberrypi.com/software/operating-systems/
3. Verify the image integrity before flashing:
```bash
   echo "<SHA256_HASH>  <filename>.img.xz" | sha256sum --check
```
4. Run the Imager, select the downloaded image via **Use Custom**, and before writing configure:
   - Hostname
   - Username and password
   - Wi-Fi credentials
   - SSH enabled with your public key (`~/.ssh/id_ed25519.pub`)
5. Flash the SD card and insert it into the Pi.

## First Boot & Access

1. Power on the Pi and wait ~2 minutes for the initial boot (filesystem resize and SSH key generation happen on first boot).
2. Find the Pi's assigned IP from your router's DHCP client list.
3. SSH into the Pi:
```bash
   ssh <YOUR_USERNAME>@<RASPBERRY_IP>
```
4. If connection fails, verify:
   - You are on the same local network
   - No VPN is active on your machine
   - Try ethernet instead of Wi-Fi for reliability

## Post-Install

1. Update the system:
```bash
   sudo apt update && sudo apt upgrade -y
```
