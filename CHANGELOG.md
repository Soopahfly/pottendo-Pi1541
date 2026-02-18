# Changelog

All notable changes to pottendo-Pi1541 are documented here.

## [1.26] - 2026-02-18

### Added
- **Power supply warning**: The Pi now detects insufficient power supply conditions
  using the VideoCore mailbox throttle status register (`TAG_GET_THROTTLED`,
  `0x00030046`).
  - A red warning banner — *"WARNING: Insufficient power supply detected!"* — is
    displayed centred at the bottom of the HDMI screen.
  - *"POWER WARNING!"* is shown on the I²C LCD (if fitted).
  - The check runs at **startup** (after the boot logo) and **continuously** during
    operation via the `UpdateScreen()` loop.
  - Triggers on under-voltage currently present (bit 0) **or** under-voltage that
    has occurred since last boot (bit 16).

### Changed
- `rpi-mailbox-interface.h`: Added `TAG_GET_THROTTLED = 0x00030046` to the
  `rpi_mailbox_tag_t` enum.
- `rpi-mailbox-interface.c`: Added `TAG_GET_THROTTLED` case handler in
  `RPI_PropertyAddTag()`.
- `main.cpp`: Added `GetThrottled()`, `CheckPowerSupply()`, throttle bit defines,
  and two call sites (startup + runtime loop).

---

## [1.25] - Prior release

- Merged upstream Pi1541 v1.19–v1.25 changes.
- Circle port improvements (pottendo, 2024).
- WebUI enhancements: USB drive support, file management, image creation/upload.
- Pico2 and ESP32 platform support.
- NTP time support, TZ option.
- Various stability and compatibility fixes.

## [1.24] and earlier

See upstream [Pi1541](https://github.com/pi1541/Pi1541) release notes and the
git log for full history of changes prior to the pottendo fork.
