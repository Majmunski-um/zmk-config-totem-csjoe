# TOTEM Cheat Sheet — Miryoku QWERTY

## Thumb keys

```
LEFT HAND                    RIGHT HAND
[Esc  / Media]  [Spc / Nav]  [Tab / Mouse]  |  [Ent / Sym]  [Bsp / Num]  [Del / Fun]
    hold=3         hold=1       hold=2            hold=5       hold=4      hold=6
```

---

## Layer 0 — Base

```
  Q    W    E    R    T        Y    U    I    O    P
  A    S    D    F    G        H    J    K    L    '
  Z    X*   C    V    B        N    M    ,    .*   /
       [Esc] [Spc] [Tab]      [Ent] [Bsp] [Del]
```

**Home-row mods** (hold, not tap):

| Key | Hold      |     | Key | Hold      |
| --- | --------- | --- | --- | --------- |
| `A` | Super/Win |     | `'` | Super/Win |
| `S` | Alt       |     | `L` | AltGr     |
| `D` | Ctrl      |     | `K` | Ctrl      |
| `F` | Shift     |     | `J` | Shift     |
| `X` | AltGr     |     | `.` | AltGr     |

> Mods only trigger on **opposite-hand** keys. Same-hand rolls always produce letters.

---

## Layer 1 — Nav (hold Space)

```
 boot  ---  ---  ---  ---      RDO  PST  CPY  CUT  UND
  GUI  ALT  CTL  SHT  ---      CAPS ←    ↓    ↑    →
  ---  RALT ---  ---  ---      INS  HOME PgDn PgUp END
        [---] [Nav] [---]      [Ret] [Bsp] [Del]
```

**Clipboard** (X11/terminal):

| Key   | Action    |
| ----- | --------- |
| `UND` | K_UNDO    |
| `CUT` | Shift+Del |
| `CPY` | Ctrl+Ins  |
| `PST` | Shift+Ins |
| `RDO` | K_AGAIN   |

---

## Layer 2 — Mouse (hold Tab)

```
 boot  ---  ---  ---  ---      RDO  PST  CPY  CUT  UND
  GUI  ALT  CTL  SHT  ---      ---  ←    ↓    ↑    →
  ---  RALT ---  ---  ---      ---  WL   WD   WU   WR
      [---] [---] [Mouse]      [MB2] [MB1] [MB3]
```

Mouse move (←↓↑→) on home row inner-to-pinkie. Scroll (WL/WD/WU/WR) on bottom row.
MB1 = left click, MB2 = right click, MB3 = middle click.

---

## Layer 3 — Media (hold Esc)

```
 boot  ---  ---  ---  ---      ---  ---  ---  ---  ---
  GUI  ALT  CTL  SHT  ---      Prev VDn  VUp  Next OUT
  ---  RALT ---  ---  ---      BT0  BT1  BT2  BT3  BCLR
      [Media] [---] [---]      [Stop] [PP] [Mute]
```

**Bluetooth**:

| Key     | Action                   |
| ------- | ------------------------ |
| `BT0-3` | Switch to BT profile 0-3 |
| `BCLR`  | Clear all BT bonds       |
| `OUT`   | Toggle USB / BLE output  |

---

## Layer 4 — Num (hold Backspace)

```
  [    7    8    9    ]        ---  ---  ---  ---  boot
  ;    4    5    6    =        ---  SHT  CTL  ALT  GUI
  `    1    2    3    \        ---  ---  ---  RALT ---
          [.]  [0]  [-]        [---] [Num] [---]
```

---

## Layer 5 — Sym (hold Enter)

```
  {    &    *    (    }        ---  ---  ---  ---  boot
  :    $    %    ^    +        ---  SHT  CTL  ALT  GUI
  ~    !    @    #    |        ---  ---  ---  RALT ---
          [(]  [)]  [_]        [Sym] [---] [---]
```

---

## Layer 6 — Fun (hold Delete)

```
 F12   F7   F8   F9  PSCRN     ---  ---  ---  ---  boot
 F11   F4   F5   F6  SLCK      ---  SHT  CTL  ALT  GUI
 F10   F1   F2   F3  PAUSE    UNLK ---  ---  RALT ---
       [App] [Spc] [Tab]      [---] [---] [Fun]
```

`UNLK` = `&studio_unlock` — unlocks ZMK Studio for live editing.

---

## ZMK Studio

1. Hold `Del` → enter Fun layer
2. Press `UNLK` (right inner bottom row)
3. Open **https://zmk.studio** in Chrome/Edge (USB) or use native app (BLE on Linux)

Studio auto-locks after ~8 min idle or on disconnect.

---

## Flashing

1. Push changes to GitHub → Actions builds automatically
2. Download `firmware.zip` from the Actions tab
3. Double-press reset on each half → drag `.uf2` file onto the drive
4. Flash `settings_reset` to both halves to clear BT bonds if needed
