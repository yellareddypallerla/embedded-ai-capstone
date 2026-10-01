# esp32-gateway

Phase 0 (runs alongside phase 1). ESP32-S3 edge node: owns the A7677S
cellular modem, publishes telemetry/alerts over MQTT.

## Scope

- Bring up the A7677S over UART/USB -- AT command init, network
  registration, PDP context (same pattern as real work, practiced here
  independently)
- Publish a simple telemetry payload over MQTT to your own broker
  (a public test broker or a local Mosquitto instance is fine for this
  project -- no need for TLS/cert infrastructure here, that's already
  covered by the real work project)
- Forward whatever the STM32 sub-device sends it (once `stm32-subdevice/`
  exists) up to MQTT too

## What this demonstrates

RTOS programming (FreeRTOS, not Linux), cellular/AT-command protocol
handling, MQTT client implementation -- the edge-connectivity layer of
the architecture.

## Status

Not started.
