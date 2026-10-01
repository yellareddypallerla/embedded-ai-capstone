# Embedded AI Capstone

Personal learning project -- entirely separate from any employer repo.
Goal: one integrated multi-tier system that genuinely needs device
drivers, kernel work, bare-metal firmware, Java (OSGi + Spring Boot),
edge AI, and full-stack web, instead of disconnected tutorials.

## The story this project tells

> Built a complete multi-tier IoT gateway from scratch -- an RTOS edge
> node with cellular connectivity, a bare-metal sub-device, a Linux SBC
> running my own kernel driver and OSGi service, YOLO-based edge video
> analytics, a full-stack monitoring dashboard, and packaged the whole
> thing as a custom Yocto image.

## Architecture

```
ESP32-S3 (FreeRTOS/bare-metal)                        esp32-gateway/
  -- owns the A7677S cellular modem (AT commands, PDP context)
  -- publishes telemetry/alerts over MQTT
        |
        | UART, self-designed frame protocol
        v
STM32G070RBT6 (bare-metal)                             stm32-subdevice/
  -- sensor read + GPIO actuator control
        |
        | UART to the Linux side
        v
CM5 + CM5 IO board (Linux -- center of gravity)
  |-- kernel driver: UART link to the STM32              kernel-driver/
  |-- OSGi Java service wrapping that driver              osgi-service/
  |-- YOLO inference on a connected camera                ai-inference/
  |-- Spring Boot API exposing sensor + detection data     backend/
  |-- React dashboard, live view                           frontend/
  |-- custom Yocto image, driver + OSGi built in            yocto-layer/
        |
Pi4   -- bring-up sandbox, then secondary validation target
BPIM5 -- tertiary validation target, proves the stack isn't board-specific
```

## What each piece demonstrates

| Component | Skill |
|---|---|
| ESP32-S3 + A7677S | RTOS, cellular/AT-command programming, edge connectivity |
| STM32G070RBT6 | Bare-metal MCU firmware, UART protocol design |
| CM5 kernel driver | Linux device driver, kernel internals |
| OSGi service | Java, modular service architecture |
| YOLO inference | Edge AI deployment, quantization, real FPS numbers |
| Spring Boot + React | Full-stack web |
| Yocto image | Custom embedded Linux build system |
| Pi4 + BPIM5 validation | Portability discipline, not a one-off hack |

## Hardware

CM5, CM5 IO board, Pi4, BPIM5, ESP32-S3, A7677S cellular modem,
STM32G070RBT6.

## Sequencing (don't run every track in parallel)

| Weeks | Focus |
|---|---|
| 1-3 | ESP32-S3 + A7677S: cellular connectivity, MQTT publish |
| 2-4 | STM32G070RBT6: bare-metal sensor/actuator firmware, UART protocol design |
| 3-6 | CM5/Pi4 kernel driver: UART link to the STM32 |
| 5-7 | OSGi service wrapping the driver |
| 6-9 | YOLO inference on a camera feed |
| 8-11 | Spring Boot API + React dashboard |
| 10-13 | Port to CM5 properly, validate on BPIM5, package as a Yocto image |
| 13-14 | Polish: architecture diagram, demo video, clean commit history |

## Status

Nothing built yet -- this is the scaffold. Fill in each folder's own
README as work actually starts there.

## Boundary with employer work

Concepts and architecture patterns learned here (OSGi structure, UART
protocol design, driver conventions) deliberately mirror the real
employer project's structure, since that's what makes the learning
transferable -- but no employer code, config, or credentials are in this
repo. This is an independent implementation built from first principles,
not a copy of anything proprietary.
