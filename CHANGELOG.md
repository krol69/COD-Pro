# Changelog

All notable changes to **BO7 PRO** (Titan Two GPC script).

## v12.1.0 — "Recoil Engine" (2026-06-15)

Major anti-recoil system upgrade implementing three best-in-class methods.

### New: Advanced Rumble Analysis
- Dual-motor weighted blend (RUMBLE_B primary for weapon fire, RUMBLE_A secondary)
- 4-tier intensity scaling: pistol/tap → SMG → AR → LMG automatic detection
- Rate-of-change tracking for first-shot kick detection

### New: Deep Pattern Learning (8-frame)
- Expanded history buffer from 4 to 8 frames
- Weighted averaging (recent frames count 3x more)
- Variance-based consistency scoring (0-100)
- Acceleration tracking detects ramping vs stabilizing recoil
- Smarter learning bonus: +15 max for consistent patterns, -6 for erratic

### New: 5-Phase Burst Compensation
- **Phase 0** (0-80ms): Initial kick — 180% pull + rumble bonus
- **Phase 1** (80-200ms): Ramp-up — smooth blend 180%→130%
- **Phase 2** (200-600ms): Sustained — 120% + consistency bonus
- **Phase 3** (600-1200ms): Fatigue — 110% stabilized pull
- **Phase 4** (1200ms+): Extended spray — minimal 100% baseline
- Horizontal drift gets 120% in early phases

### Improved
- Output smoothing: exponential filter prevents jerky corrections
- ADS-scaled intensity: 80-100% based on trigger depth
- Better state reset between bursts
- New runtime variables for phase/consistency/acceleration tracking

---

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
