tl;dr Hardware enablement still needs to happen, but very promising

## Works (both Fedora 40 & Rawhide/41)

- [x] NVMe
- [x] Internal display + brightness controls
- [x] Keyboard with the usual hot keys (not all)
- [x] WiFi & Bluetooth (Intel AX211)
- [x] Display out (USB-C display, did not test Thunderbolt/USB4)
- [x] Keyboard backlight
- [x] Power limits
- [x] Power profiles
- [x] Suspend, plugged in & unplugged while suspended
- [x] s2idle (modern standby)

## Broken

- [x] ~~Fingerprint reader (no surprise)~~ ~~Works with a patch to libfprint!~~ [Patch merged](https://gitlab.freedesktop.org/libfprint/libfprint/-/merge_requests/494)
- [x] ~~Touch screen~~ FIXED: https://github.com/quo/ithc-linux (use `sl6` branch for now)
- [x] ~~Trackpad (haptic, clickpad probably works)~~ FIXED: https://github.com/ty2/goodix-gt7868q-linux-driver
- [x] ~~Internal speakers (Sound card shows up, volume controls work, no sound)~~ FIXED: https://github.com/thesofproject/linux/issues/5036#issuecomment-2148594209
- [ ] Mic mute hot key led
- [ ] Cameras (both normal & IR) -- probably that IPU6 garbage
- [ ] Fn+Q (UEFI power/fan profile things), appears to have no effect
- [x] ~~Seemingly low refresh rate (almost like VRR is on, but the compositor doesn't have it on)~~ FIXED: disable PSR `i915.enable_psr=0`
- [x] ~~remap copilot key~~ FIXED: install [keyd](https://github.com/rvaiya/keyd) with `leftmeta+leftshift = layer(meta)`

## Misc

- Night light (f.lux for Gnome) was broken out of the box, selecting a color profile for the internal display resolves this issue

## Noteworthy

- Appears to idle at ~6 watts at full brightness
  - Did not test under load, but probably similar to Windows here
  - Power limit setting with power profiles is probably the superior battery life approach
  - Battery stats & conservation mode is available via ideapad_laptop

Hopefully after a few more kernel cycles the hardware enablement trickles in.

Probe: http://linux-hardware.org/?probe=eface5275d 
