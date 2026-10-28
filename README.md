# OpenWrt firmware for Xiaomi Redmi Router AC2100

Automated OpenWrt builds for the Xiaomi Redmi Router AC2100 (model R2100) using GitHub Actions. The build workflow and package selection are based on [OpenWrt-Newifi_D2](../OpenWrt-Newifi_D2), with the device profile and wireless modules configured for the Redmi AC2100.

## Device profile

- SoC: MediaTek MT7621
- 2.4 GHz: MediaTek MT7603EN
- 5 GHz: MediaTek MT7615N
- OpenWrt profile: `ramips/mt7621`, `xiaomi_redmi-router-ac2100`

The Redmi AC2100 and Newifi D2 share the MT7621 platform, but their wireless hardware differs. This project selects the Redmi profile and its MT7603/MT7615 drivers instead of reusing the D2 device profile.

## Build

1. Create a GitHub repository from this project and push the files.
2. Open **Actions → Build OpenWrt Redmi AC2100 → Run workflow**.
3. Download the resulting firmware from the workflow artifacts or release.

The build uses the `janethan/lede` repository on its `master` branch, matching the D2 project.

## Configuration

- `.config` selects `xiaomi_redmi-router-ac2100` and carries over the D2 project's package choices.
- `diy-part1.sh` adds the same `helloworld` feed as the D2 project.
- `diy-part2.sh` keeps the D2 defaults (LAN address `192.168.100.1` and Argon theme) and sets the hostname to `Redmi-AC2100`.

Review the firmware source and device installation instructions before flashing. Firmware has not been built or tested on physical hardware as part of creating this project.
