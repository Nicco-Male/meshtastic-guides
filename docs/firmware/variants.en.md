# Firmware variants (Italy)

In Italy you’ll most commonly encounter two “families”:

1) **Official Meshtastic firmware (upstream)**  
2) **LoraItalia patched firmware** (a fork based on Meshtastic)

---

## Key limitation
Meshtastic **does not support OTA updates over LoRa**. Firmware updates require USB / DFU / a flasher depending on your device.

---

## 1) Official Meshtastic firmware
Meshtastic publishes:
- **Beta** releases (recommended for most users)
- **Alpha** releases (newer features, higher risk)

Typical flashing methods:
- **Web flasher** (recommended for ESP32)
- **UF2 drag & drop** for many nRF52 / RP2040 devices

---

## 2) LoraItalia patched firmware
A Meshtastic-based firmware with Italy-focused patches (MQTT defaults, neighbor behavior, community-specific tweaks, etc.).  
Follow LoraItalia’s notes carefully, especially for MQTT gateways.

---

## Quick pick
- Choose **official Meshtastic** for upstream stability/support and neutral defaults.
- Choose **LoraItalia** if you want the Italy ecosystem defaults and their recommended patches.

---

## Sources
- https://meshtastic.org/docs/faq/
- https://meshtastic.org/downloads/
- https://meshtastic.org/docs/getting-started/flashing-firmware/
- https://www.loraitalia.it/firmware-loraitalia/
- https://github.com/LoraItalia/loraitalia-firmware
