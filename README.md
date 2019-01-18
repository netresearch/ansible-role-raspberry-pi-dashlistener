# Ansible roles for the Raspberry Pi dashbutton listener

## Requirements

Ansible >= 2.5

Raspbian (with ssh-server enabled and key copied) >= stretch

## Setting up a Raspberry Pi

 1. Download the image "Raspbian Stretch with Desktop" from `https://www.raspberrypi.org/downloads/raspbian/`.
 2. Unzip the .zip file which contains the image with `The Unarchiver (Mac) or Unzip (Linux)`.
 3. Download Etcher from `https://www.balena.io/etcher/` and install it.
 4. Connect an SD card reader with the SD card inside.
 5. Open Etcher and select from your hard drive the Raspberry Pi .img file you wish to write to the SD card.
 6. Select the SD card you wish to write your image to.
 7. Review your selections and click 'Flash!' to begin writing data to the SD card.
 8. Open a terminal, change into the boot directory of the µSD-card and execute `sudo touch ssh`.
 9. Put the µSD-card into the Pi and plug in the µ-USB-cable for power.
10. Open a terminal with `Alt + Ctrl + F1` and type `ssh-keygen` and press `Enter` 3 times.
11. `Enjoy!`

## Files

Customize the file files/dash-listener-config.json

## Variables

| variable   | state           | example       |
| ---------- | --------------- | ------------- |
| wifi_name  | "wifi-name"     | "YOUR-SSID"   |
| wifi_psk   | "wifi-password" | "YOUR-PASS"   |

## Example playbook

```yaml
- name: Configure raspberry pi as dashlistener
  hosts: dashlistener.netresearch.nr
  tasks:
    - name: Configure dashbutton-listener
      include_role:
        name: raspberry-pi-dashlistener
      vars:
        wifi_name: "HomeSweetHome"
        wifi_psk: "A8B7C6D5E4F3G2H1"
```
