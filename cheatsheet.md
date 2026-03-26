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
  Z    X    C    V    B        N    M    ,    .    /
       [Esc] [Spc] [Tab]      [Ent] [Bsp] [Del]
```

**Home-row mods** (hold, not tap):

| Key | Hold      |     | Key | Hold      |
| --- | --------- | --- | --- | --------- |
| `A` | Super/Win |     | `'` | Super/Win |
| `S` | Alt       |     | `L` | Alt       |
| `D` | Ctrl      |     | `K` | Ctrl      |
| `F` | Shift     |     | `J` | Shift     |

> Mods only trigger on **opposite-hand** keys. Same-hand rolls always produce letters.

---

## Layer 1 — Nav (hold Space)

```
  ---  ---  ---  ---  ---      RDO  PST  CPY  CUT  UND
  GUI  ALT  CTL  SHT  ---      CAPS ←    ↓    ↑    →
  ---  ---  ---  ---  ---      INS  HOME PgDn PgUp END
        [---] [Nav] [---]      [Ret] [Bsp] [Del]
```

**Clipboard** (CUA bindings):

| Key   | Action    |
| ----- | --------- |
| `UND` | Ctrl+Z    |
| `CUT` | Ctrl+X    |
| `CPY` | Ctrl+C    |
| `PST` | Ctrl+V    |
| `RDO` | K_AGAIN   |

---

## Layer 2 — Mouse (hold Tab)

```
  ---  ---  ---  ---  ---      RDO  PST  CPY  CUT  UND
  GUI  ALT  CTL  SHT  ---      ---  ←    ↓    ↑    →
  ---  ---  ---  ---  ---      ---  WL   WD   WU   WR
      [---] [---] [Mouse]      [MB2] [MB1] [MB3]
```

Mouse move (on home row) and scroll (on bottom row) mirror Nav arrow layout.
MB1 = left click (middle thumb), MB2 = right click (inner thumb), MB3 = middle click (outer thumb).

---

## Layer 3 — Media (hold Esc)

```
  ---  ---  ---  ---  ---      ---  ---  ---  ---  ---
  GUI  ALT  CTL  SHT  ---      OUT  Prev VDn  VUp  Next
  ---  ---  ---  ---  ---      BCLR BT0  BT1  BT2  BT3
      [Media] [---] [---]      [Stop] [PP] [Mute]
```

**Bluetooth**:

| Key     | Action                   |
| ------- | ------------------------ |
| `BT0-3` | Switch to BT profile 0-3 |
| `BCLR`  | Clear current BT profile |
| `OUT`   | Toggle USB / BLE output  |

---

## Layer 4 — Num (hold Backspace)

```
  [    7    8    9    ]        ---  ---  ---  ---  ---
  ;    4    5    6    =        ---  SHT  CTL  ALT  GUI
  `    1    2    3    \        ---  ---  ---  ---  ---
          [.]  [0]  [-]        [---] [Num] [---]
```

---

## Layer 5 — Sym (hold Enter)

```
  {    &    *    (    }        ---  ---  ---  ---  ---
  :    $    %    ^    +        ---  SHT  CTL  ALT  GUI
  ~    !    @    #    |        ---  ---  ---  ---  ---
          [(]  [)]  [_]        [Sym] [---] [---]
```

---

## Layer 6 — Fun (hold Delete)

```
 F12   F7   F8   F9  PSCRN     ---  ---  ---  ---  ---
 F11   F4   F5   F6  SLCK      ---  SHT  CTL  ALT  GUI
 F10   F1   F2   F3  PAUSE    UNLK  ---  ---  ---  ---
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
