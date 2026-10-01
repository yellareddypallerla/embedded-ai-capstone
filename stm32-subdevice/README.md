# stm32-subdevice

Phase 0-1 (runs alongside kernel-driver/). STM32G070RBT6 bare-metal
firmware: reads a sensor, controls a GPIO actuator, talks UART to the
Linux side (CM5/Pi4).

## Scope

- Simple, self-designed UART frame protocol (this is your own design --
  practice the same "design the communication protocol" skill that's on
  your real work task list, here first, on something you fully control)
- Sensor read (whatever's on hand -- a basic I2C/analog sensor is enough)
- GPIO actuator control (an LED or relay is enough to demonstrate the
  pattern)
- Bonus, once comfortable: an OTA update path over the same UART link,
  mirroring the real `ned_stm32_fota` pattern

## What this demonstrates

Bare-metal MCU firmware, UART protocol design, the sub-device half of a
gateway architecture -- directly parallels real work structure, built
independently first.

## Status

Not started.
