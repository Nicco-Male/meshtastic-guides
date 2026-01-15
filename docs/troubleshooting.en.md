# Troubleshooting & FAQ

Quick fixes for the most common Meshtastic issues. If the problem persists, collect **logs**, **app/firmware version**, and **device model** before opening an issue.

## App connection (Bluetooth/Wi‑Fi)

**Symptoms**: device not visible, pairing fails, unstable connection.

**Quick fixes**:
- Toggle Bluetooth (or Wi‑Fi) and restart the app.
- Ensure the device is not already connected to another phone.
- Update to the latest compatible app and firmware.
- On Android, allow **Location** permission for BLE scanning.
- On iOS, check Bluetooth permissions in Settings.

## GPS won’t lock

**Symptoms**: no position or very slow updates.

**Quick fixes**:
- Wait a few minutes outdoors (first fix is slower).
- Confirm the GPS antenna is connected and supported by the board.
- Ensure the GPS module is enabled in configuration.

## MQTT not receiving data

**Symptoms**: no messages on the broker or empty topics.

**Quick fixes**:
- Recheck **broker, port, username/password**.
- Confirm the device has Internet connectivity.
- Validate **topic** and namespace configuration.
- Test with an external MQTT client (e.g., mosquitto_sub) to isolate the issue.

## Poor range test

**Symptoms**: few nodes visible, lost packets.

**Quick fixes**:
- Inspect **antenna**, connectors, and correct frequency.
- Avoid obstacles and test with line-of-sight.
- Reduce data rate or use more robust LoRa presets.
- Ensure all nodes share the same **region** and compatible **presets**.

## When to open an issue

Before reporting a bug, include:
- App and firmware versions.
- Device model and LoRa region.
- Steps to reproduce.
- Relevant logs or screenshots.
