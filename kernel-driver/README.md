# kernel-driver

Phase 1. Start on the Pi4, not the CM5 -- better documentation/community
for driver bring-up, and you don't want to brick your primary board while
still learning.

## Order to learn in

1. **Character driver** -- simplest possible: `open`/`read`/`write` on a
   `/dev/` node, no real hardware yet. Confirms your toolchain, module
   loading (`insmod`/`rmmod`), and `dmesg` workflow all work.
2. **Platform driver** -- bind to a device-tree node instead of being
   manually loaded. This is the pattern real peripherals use.
3. **Real peripheral driver** -- I2C or SPI sensor, or a camera driver if
   going straight for the AI-inference use case. Pick whichever sensor/
   camera you actually have on hand for the CM5 IO board.

## Reference

- Bootlin's training slides (bootlin.com/training) -- current, free,
  much better than most paid courses for this specific stack
- "Linux Device Drivers" (LDD3, free online) -- dated APIs in places but
  the concepts (char/platform driver structure, interrupt handling) hold

## Status

Not started.
