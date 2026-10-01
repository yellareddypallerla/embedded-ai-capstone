# Embedded AI Capstone

Personal learning project -- entirely separate from any employer repo.
Goal: one integrated project that genuinely needs device drivers, kernel
work, Java (OSGi + Spring Boot), edge AI, and full-stack web, instead of
five disconnected tutorials.

## The story this project tells

> Wrote a kernel driver for a camera/sensor on an embedded Linux board,
> wrapped it as an OSGi service, ran YOLO inference on the captured
> frames, exposed the results over a Spring Boot API, and built a React
> dashboard to visualize it live -- then packaged the whole thing as a
> custom Yocto image.

## Architecture

```
[Sensor/Camera] --> [Kernel driver, C]              kernel-driver/
        |
        v
[OSGi Java service wraps the driver]                osgi-service/
        |
        v
[YOLO inference on the captured frames]              ai-inference/
        |
        v
[Spring Boot REST API exposes live data]             backend/
        |
        v
[React dashboard shows live detections + sensor      frontend/
 data, updating in real time]
        |
(capstone polish)
[Custom Yocto image packaging all of the above]       yocto-layer/
```

## Hardware

- **CM5 + CM5 IO board** -- primary target (matches real work hardware,
  skills transfer directly)
- **Pi4** -- sandbox for early/risky driver bring-up (better docs/
  community than CM5), so the primary board doesn't get bricked while
  learning
- **BPIM5** -- secondary validation target, proving the work isn't
  board-specific

## Sequencing (don't run all tracks in parallel)

| Weeks | Focus |
|---|---|
| 1-4 | Kernel driver on Pi4 (char/platform driver basics, then a real sensor/camera driver) |
| 3-6 | OSGi wrapper in Java around the driver |
| 5-8 | YOLO inference (quantized, e.g. TFLite/ONNX Runtime) on captured frames |
| 7-10 | Spring Boot API + React dashboard exposing/visualizing the above |
| 9-12 | Port to CM5, validate on BPIM5, package as a Yocto image |

## Status

Nothing built yet -- this is the scaffold. Fill in each folder's own
README as work actually starts there.

## Boundary with employer work

This project is intentionally separate from the OSGi driver bundles
being built for the actual employer project (STM32/RS485/USB/GPIO
drivers for BPIM5, handed over to the software team). Concepts learned
here (OSGi patterns, driver structure) inform that work, but no code,
config, or credentials cross between the two. See the employer repo's
own `Device-services/PI/osgi-hw-drivers/README.md` for that separate,
real deliverable.
