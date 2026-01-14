# MQTT servers & credentials (EN)

This page is intentionally **minimal** (English is present, but Italian is primary).

Key point: **do not commit real passwords to a public repo**. Use placeholders or environment variables.

## Meshtastic public broker (default)

Defaults:
- Address: `mqtt.meshtastic.org`
- Username: `meshdev`
- Password: `large4cats`

The public broker applies restrictions (zero-hop policy, filtering, reduced position precision).

## LoraItalia

LoraItalia describes gateway nodes that route traffic to an MQTT broker, and their custom firmware sets a default MQTT topic “ready” for the Italian server.

Broker host/user/pass are not included here unless clearly published officially.
