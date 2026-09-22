# Firmware binaries

Version follows Node32-HUB.

## Current release

- **v1.114**: `n16r8_v1.114_CAM_20260921_0148.zip` (also on GitHub Releases)

## Build

Compile inside [Node32-HUB](https://github.com/nasp2000/Node32-HUB) with the `Cam-M` pack:

```bash
cd chatgpt
pio run -e n16r8
```

Post-build output (created by `rename_firmware.py`):

```
build/esp32s3/CAM/v1.114/<YYYYMMDD_HHMM>/
  n16r8_v1.114_CAM_<YYYYMMDD_HHMM>.bin     # + bootloader.bin, partitions.bin, flash_command.txt
  LICENSE, SBOM.md, THIRD_PARTY_NOTICES, README_DISTRIBUTION.txt, third-party.zip
```

## Release

1. Zip `bootloader.bin`, `partitions.bin`, `.bin` and `flash_command.txt` (from the build folder above) → `n16r8_v1.<ver>_CAM_<YYYYMMDD_HHMM>.zip`
2. Include the compliance set: `LICENSE`, `SBOM.md`, `THIRD_PARTY_NOTICES`, `README_DISTRIBUTION.txt`, `third-party.zip`
3. Place the `.zip` here locally in `firmware/`, commit and push — the GitHub release is created from it (the zip itself is not kept on the remote `firmware/` folder)

## Flash

- **First-time**: use [webflasher_Node32-HUB](https://github.com/nasp2000/webflasher_Node32-HUB) (select `n16r8_v1.114_CAM_20260921_0148.zip`)
- **Updates**: OTA at `http://<esp32-ip>/ota` (upload only the `.bin` file)