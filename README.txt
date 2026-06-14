COD Pro - BO7 Titan Two Script
================================
v11.0.0 | Ultra Responsive Edition | Latest Patch

Original by Fadexz | Reworked for BO7


QUICK SETUP
===========
1. Load "COD Pro.gpc" onto Titan Two via Gtuner IV
2. Play - all features ON, presets ready


NEW IN v11.0.0
==============

SMART ANTI-RECOIL (Pattern Learning)
  The script now tracks rumble patterns across frames and "learns"
  your weapon's recoil behavior. Consistent patterns get boosted,
  erratic patterns get reduced. No manual tuning needed.

WEAPON PRESETS (Hold LT + D-Pad)
  Quick switch between optimized profiles:
  • D-Pad UP    = AR (balanced: 32 vert, 75% adapt)
  • D-Pad RIGHT = SMG (light: 22 vert, 60% adapt)
  • D-Pad DOWN  = LMG (heavy: 45 vert, 85% adapt)
  • D-Pad LEFT  = Custom (your current settings)

1MS ULTRA RESPONSE MODE
  Enable in Settings menu for 1000Hz polling.
  Maximum responsiveness for competitive play.

OLED MENU DISPLAY
  Visual menu on Titan Two screen with organized pages:
  • Main Menu -> Anti-Recoil / Movement / Settings
  • Real-time value display
  • Feature status overview


FEATURES (ALL ON BY DEFAULT)
============================
1. Smart Anti-Recoil  - Adaptive + pattern learning
2. Slide Cancel       - BO7 optimized (3 modes)
3. Bunny Hop          - Frame-perfect chaining
4. Snake Movement     - Evasive rapid strafe


CONTROLS
========

QUICK TOGGLES:
  Anti-Recoil    : Hold LT + tap XBOX/PS
  Slide Cancel   : Hold LB + tap RB
  Bhop           : Hold LB + tap VIEW/SHARE
  Snake          : Hold LB + tap OPTIONS/MENU

WEAPON PRESETS (Hold LT + D-Pad):
  D-Pad UP       : AR Profile
  D-Pad RIGHT    : SMG Profile
  D-Pad DOWN     : LMG Profile
  D-Pad LEFT     : Custom Profile

MENU:
  Open           : Hold LT + tap MENU (no LB held)
  Navigate       : D-Pad UP/DOWN
  Adjust         : D-Pad LEFT/RIGHT
  Select/Toggle  : A / CROSS
  Back/Close     : B / CIRCLE


MENU STRUCTURE
==============

MAIN MENU
  > Anti-Recoil
  > Movement
  > Settings
  > Exit

ANTI-RECOIL PAGE
  Enable         [ON/OFF]
  Vertical       0-100    (default 32)
  Horizontal     -50 to 50 (default 0)
  Adaptive       0-100    (default 75)
  < Back

MOVEMENT PAGE
  Slide          [ON/OFF]
  Bhop           [ON/OFF]
  Snake          [ON/OFF]
  SC Delay       150-400ms (default 240)
  SC Mode        0-2       (default 0)
  BH Time        30-80ms   (default 45)
  < Back

SETTINGS PAGE
  SN Speed       5-25      (default 12)
  SN Range       15-60     (default 35)
  Preset         AR/SMG/LMG/CUST
  1ms Mode       [ON/OFF]
  < Back


SLIDE CANCEL MODES
==================
Mode 0: BO7 ADS Cancel (default) - Slide, ADS tap, jump
Mode 1: Jump Cancel - Slide, jump
Mode 2: Legacy - Double slide, jump


LED INDICATORS
==============
WHITE   : Normal gameplay
BLUE    : Menu navigation
GREEN   : Feature ON / value up / preset switch
RED     : Feature OFF


ABOUT AI FEATURES
=================
The "pattern learning" anti-recoil is a standalone simulation.
For true AI aim assist (like PhantomCV), you need:
  - PC running Python + capture software
  - GCV (Game Capture Video) connection
  - Trained model (YOLOv5 etc.)

This script works 100% standalone on the Titan Two.


COMPATIBILITY
=============
Platform   : PC / PlayStation / Xbox (via Titan Two)
Game       : Call of Duty: Black Ops 7 (Latest Patch)
Controller : Any (Xbox default, PS auto-remapped)
Display    : Titan Two OLED supported
Polling    : 250Hz default / 1000Hz ultra mode


LICENSE
=======
GNU General Public License v3
