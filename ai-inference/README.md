# ai-inference

Phase 3. YOLO inference on frames coming from `osgi-service/`. Aim for
**deployment** skill, not ML research depth -- quantization and real
on-device latency/FPS numbers are what interviewers actually probe.

## Plan

1. Pick a pretrained YOLO variant (start small -- YOLOv8n or similar,
   not a huge model that won't run on-device at all)
2. Quantize to INT8 via TFLite or ONNX Runtime
3. Run on CM5/Pi4 CPU first, measure real FPS/latency
4. If the board has an NPU/GPU path, try hardware acceleration and
   compare -- the *comparison* is the interesting interview story, not
   just "it runs"

## What "done" looks like

A script that takes frames from the OSGi service (or a test video while
that's not ready yet), runs detection, and outputs results with a
measured FPS number -- not just "it works on one image."

## Status

Not started. Can be prototyped against a test video file independently
of `kernel-driver/`/`osgi-service/` being finished -- doesn't have to
wait in the sequence if you want to parallelize this specific piece.
