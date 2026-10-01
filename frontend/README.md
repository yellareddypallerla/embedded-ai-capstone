# frontend

Phase 4b. React dashboard consuming `backend/`'s API -- shows live
sensor data and YOLO detections.

## Minimal scope

- One page, polling (or WebSocket once backend supports it) the backend
  for latest readings/detections
- Simple list/table is fine for v1 -- don't spend time on design polish
  until the data is actually flowing live

## Status

Not started. Depends on `backend/` having real endpoints -- can be built
against mocked JSON responses first to avoid blocking on backend being
finished.
