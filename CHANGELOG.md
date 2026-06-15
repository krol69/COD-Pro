# Changelog

All notable changes to **BO7 PRO** (Titan Two GPC script).

## v12.0.0 — "Foundation" (2026-06-15)

A ground-up correctness pass. Earlier versions mixed two different Titan Two
languages (legacy GPC + GPC2) and used invented functions, so they would not
compile cleanly in Gtuner IV. This release commits to a single, verified
dialect.

### Fixed (real compile/runtime bugs)
- **Single dialect:** the whole script is now native **GPC2**.
- **Added `#include <xb1.gph>`** — the `XB1_*` identifiers were being used with
  no header, so they would not resolve.
- **Replaced invented OLED calls** (`print_oled`, `printf_oled`, wrong-arg
  `rect_oled`) with the real API: `cls_oled`, `print`, `rect_oled`, `line_oled`.
- **`vm_tctrl` is relative** to a 10ms default (negative = faster). The old
  `vm_tctrl(0)` ran the VM at ~10ms (high latency). Now `-9` (~1ms) / `-6` (~4ms).
- **Typed functions** (`void` / `int`) instead of the legacy `function` keyword.
- **`pmem` slot spacing** corrected to 4 bytes per value.
- No string literals are passed as parameters (a GPC2 limitation); the OLED
  helpers handle geometry only and all text is inline in `print()`.

### Changed / Improved
- Numeric menu values now render as **fill bars** (clean, readable, and uses
  only verified OLED primitives — no int-to-string needed).
- Tighter combo timing: 14ms tap / 26ms gap.
- Faster defaults: 220ms slide cancel, 40ms bhop.

### Features (all enabled by default)
- Smart Anti-Recoil (rumble-adaptive + pattern learning)
- Slide Cancel (BO7 / Jump / Legacy)
- Bunny Hop
- Snake Movement
- OLED menu, weapon presets (AR/SMG/LMG/Custom), persistent settings, LED feedback

### ⚠️ Verification status (read before relying on it)
This was authored without a Gtuner IV compiler on hand. The **core**
(get_val/set_val, event_press, combos, get_rumble, pmem, led_set, vm_tctrl) is
matched to real, working Titan Two scripts. The **OLED layer** is matched to the
documented API but should be compiled once in Gtuner IV. If anything errors it
will almost certainly be one of:
- an OLED constant name (`OLED_FONT_SMALL/MEDIUM`, `OLED_WHITE/BLACK`)
- the exact `xb1.gph` include name for your platform

See `README.txt` → "Verifying on device" for a 60-second checklist.

---

## v11.x and earlier
Rapid feature iterations (recoil, slide cancel, bhop, snake, wall bounce,
weapon presets, pattern-learning recoil, OLED experiments). Superseded by v12's
correctness rewrite. The last full-featured legacy build is preserved as
`COD Pro.gpc.backup`.
