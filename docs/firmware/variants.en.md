# Firmware variants (Italy)

In Italy you will most commonly see **two options**:

1) **Official Meshtastic firmware**
2) **LoraItalia firmware (with patches)**

---

## Key rule: how updates work

Meshtastic **does not update OTA over LoRa**. Firmware updates require **USB / DFU / a flasher** depending on your device.

---

## 1) Official Meshtastic firmware
- **Beta**: recommended for regular use
- **Alpha**: newer changes, higher risk

Flashing depends on hardware (ESP32 vs nRF52, etc.). Always make a config backup first.

---

## 2) LoraItalia firmware (patches)
A Meshtastic-based firmware with Italy-oriented changes (MQTT defaults, community guidance, etc.).  
If you connect nodes to MQTT, follow LoraItalia operational recommendations to avoid adding noise to the mesh.

---

## Sources
- https://meshtastic.org/docs/
- https://www.loraitalia.it/
