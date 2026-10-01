# yocto-layer

Phase 5 -- capstone polish. Package the kernel driver (and ideally the
OSGi service) into a custom Yocto image for the CM5. This is the part
most embedded engineers skip, and the strongest differentiator in the
whole project.

## Plan

- Custom layer containing a recipe for the `kernel-driver/` module
- Image boots on CM5 with the driver built in, not manually insmod'd
- Stretch goal: include the OSGi runtime (Felix) + service bundle in the
  image too, so the board boots directly into the full pipeline

## Reference

- Yocto Project Mega-Manual (official docs) for layer/recipe/bitbake
  fundamentals
- `devtool` workflow for iterating on a recipe without a full rebuild
  every time

## Status

Not started. Last phase -- do this once the driver and OSGi service are
both solid on CM5, not before.
