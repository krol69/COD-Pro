BO7 PRO - Titan Two GPC Script
==============================
v12.2.0 "Live Tuning"  |  Native GPC2  |  Black Ops 7

Original by Fadexz | Reworked for BO7


WHAT THIS IS
============
A clean, single-language (GPC2) Titan Two script for Black Ops 7 with:
  1. Smart Anti-Recoil  (8-frame pattern learning, 5-phase burst compensation)
  2. Slide Cancel       (BO7 / Jump / Legacy modes)
  3. Bunny Hop          (hold jump to auto-chain)
  4. Snake Movement     (evasive strafe while prone)
Plus OLED menu with scrolling, Live HUD, quick-tune, weapon presets,
persistent settings, and LED feedback.

All four features are ON by default.


SETUP
=====
1. Open Gtuner IV on your PC.
2. Compile "COD Pro.gpc"  (Compiler > Build, or F7).
3. Program it to a Titan Two memory slot (Device > Program).
4. Play. Settings save automatically and persist between sessions.


PLATFORM
========
This file uses Xbox identifiers via  #include <xb1.gph>.
PlayStation users: change the include to <ps5.gph> (or <ps4.gph>) and swap the
XB1_* names for PS5_*/PS4_*:

  XB1_RT -> PS_R2     XB1_LT -> PS_L2     XB1_RB -> PS_R1   XB1_LB -> PS_L1
  XB1_A  -> PS_CROSS  XB1_B  -> PS_CIRCLE XB1_X  -> PS_SQUARE XB1_Y -> PS_TRIANGLE
  XB1_LS -> PS_L3     XB1_RS -> PS_R3
  XB1_MENU -> PS_OPTIONS   XB1_VIEW -> PS_SHARE/CREATE   XB1_XBOX -> PS_PS
  XB1_LX/LY/RX/RY -> PS_LX/LY/RX/RY   XB1_UP/DOWN/LEFT/RIGHT -> PS_UP/...


CONTROLS
========
QUICK TOGGLES (LED flashes green=ON / red=OFF):
  Anti-Recoil   : Hold LT + tap XBOX/PS
  Slide Cancel  : Hold LB + tap RB
  Bhop          : Hold LB + tap VIEW/SHARE
  Snake         : Hold LB + tap MENU/OPTIONS

QUICK-TUNE (adjust mid-game, no menu):
  Hold LT + click RS + D-Pad:
    UP/DOWN     = Vertical +/-5
    LEFT/RIGHT  = Adaptive +/-10
  Visual bar shows current value. Settings save automatically.

WEAPON PRESETS (Hold LT + D-Pad, without RS):
  UP = AR    RIGHT = SMG    DOWN = LMG    LEFT = Custom

MENU (Hold LT + tap MENU, with LB released):
  Navigate      : D-Pad UP / DOWN
  Adjust value  : D-Pad LEFT / RIGHT
  Select/Toggle : A / CROSS
  Back / Close  : B / CIRCLE
  LED is BLUE while the menu is open. Scrolling pages show ^/v indicators.

LIVE HUD (Settings > Live HUD: ON):
  While firing, OLED shows: Phase (0-4), Consistency, Rumble, Pull strength.
  Turn OFF in Settings if you prefer status-only display.


MENU MAP
========
MAIN -> Anti-Recoil / Movement / Settings / Exit

  ANTI-RECOIL : Enable | Vertical 0-100 | Horizontal -50..50 | Adaptive 0-100
  MOVEMENT    : Slide | Bhop | Snake | SC Delay 150-400 | SC Mode | BH Time 25-80
  SETTINGS    : SN Speed 5-25 | SN Range 15-60 | Preset | 1ms Mode | Live HUD

SC Mode:  BO7 (ADS cancel) / JUMP / LEG (legacy double-slide)


DEFAULTS
========
Vertical 30 | Horizontal 0 | Adaptive 70%
Slide delay 220ms (BO7 mode) | Bhop 40ms
Snake speed 12 / range 30 | Preset AR | 1ms mode ON | Live HUD ON


TUNING TIPS
===========
Gun still climbs?        raise Vertical
Over-corrects (pulls down)? lower Vertical
Drifts left/right?       set Horizontal (- left, + right)
Slide cancel too slow?   lower SC Delay
Bhop skips jumps?        raise BH Time
Snake too twitchy?       lower SN Speed / SN Range


HOW THE "SMART" ANTI-RECOIL WORKS  (no screen needed)
=====================================================
It reads your controller's RUMBLE (the vibration the game sends when you fire).
Different guns vibrate differently, so the script estimates recoil strength and
adapts in real time. It also tracks the last few rumble readings: steady
patterns get a little extra pull, erratic ones get eased off. This is 100%
on-device - no capture card, no PC vision, nothing to see your screen.


VERIFYING ON DEVICE (60 seconds)
================================
This version was written without a compiler on hand, so compile it once:
  1. In Gtuner IV press F7 (Build). It should report 0 errors.
  2. If it flags an OLED constant, it's almost certainly a name:
       OLED_FONT_SMALL / OLED_FONT_MEDIUM, OLED_WHITE / OLED_BLACK.
     Open the Gtuner "GPC Language Reference" and match the exact names.
  3. If it flags the include, confirm your device header name (xb1.gph for Xbox).
  4. Plug in, watch the OLED show "BO7 PRO v12.0", then test each toggle.
See CHANGELOG.md for the full list of what changed and why.


FILES
=====
COD Pro.gpc        - the script (GPC2)
CHANGELOG.md       - version history + verification status
COD Pro.gpc.backup - last full legacy build (reference only)
LICENSE            - GNU GPL v3


LICENSE
=======
GNU General Public License v3 - see LICENSE.
