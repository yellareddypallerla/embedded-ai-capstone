# backend

Phase 4a. Spring Boot REST API exposing live sensor + detection data from
`osgi-service/` and `ai-inference/`. Reinforces the same Java you're
learning for OSGi, in a different context (web backend) -- also doubles
as literacy for reading ThingsBoard's own Spring Boot backend later.

## Minimal scope

- One endpoint for latest sensor reading
- One endpoint for latest detection results (what YOLO found, confidence,
  timestamp)
- Keep it to plain REST first -- add WebSocket/SSE for real-time push
  only once the basic polling version works end to end

## Status

Not started. Depends on `osgi-service/` and `ai-inference/` having
something real to expose -- can stub both with fake data early to build
the API shape before the real pieces are ready.
