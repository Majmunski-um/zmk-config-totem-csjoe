# ZMK config for the TOTEM split keyboard

[Hardware files & build guide](https://github.com/GEIGEIGEIST/totem) &nbsp;·&nbsp;
[ZMK firmware](https://zmk.dev/) &nbsp;·&nbsp;
[ZMK Studio](https://zmk.studio/)

TOTEM is a 38-key column-staggered wireless split keyboard powered by two
[Seeed XIAO BLE](https://wiki.seeedstudio.com/XIAO_BLE/) (nRF52840) controllers.

---

## Layout — Miryoku QWERTY

This config uses [Miryoku](https://github.com/manna-harbour/miryoku), an ergonomic
layer system designed for keyboards with 3x5 + 3-thumb keys per hand.

Variant options used:
- **Alphas:** QWERTY
- **Nav:** Default (`caps_word LEFT DOWN UP RIGHT` on home row)
- **Clipboard:** Default X11/terminal (`K_UNDO`, `Shift+Ins`, `Ctrl+Ins`, `Shift+Del`, `K_AGAIN`)

### Home-row mods (GACS order)

Hold a home-row key to activate a modifier instead of tapping the letter.

| Finger | Left key | Modifier       | Right key | Modifier |
| ------ | -------- | -------------- | --------- | -------- |
| Pinkie | `A`      | `LGUI` (Super) | `'`       | `RGUI`   |
| Ring   | `S`      | `LALT`         | `L`       | `RALT`   |
| Middle | `D`      | `LCTRL`        | `K`       | `RCTRL`  |
| Index  | `F`      | `LSHFT`        | `J`       | `RSHFT`  |

Bottom-row ring keys (`X` and `.`) also have `RALT` (AltGr) on hold.

### Thumb keys

```
Left:   [Esc/Media]  [Space/Nav]  [Tab/Mouse]
Right:  [Enter/Sym]  [Bksp/Num]   [Del/Fun]
```

Tap for the primary key, hold to activate the named layer.

### Layers

| #   | Name         | Thumb to activate | Purpose                                         |
| --- | ------------ | ----------------- | ----------------------------------------------- |
| 0   | **Base**     | --                | QWERTY + home-row mods                          |
| 1 | **Nav** | Hold `Space` | Arrows, caps_word, Home/End/PgUp/PgDn, clipboard |
| 2 | **Mouse** | Hold `Tab` | Mouse move, scroll (4-way), MB1/MB2/MB3 |
| 3   | **Media**    | Hold `Esc`        | Vol, prev/next, BT profiles, OUT_TOG, BT_CLR    |
| 4   | **Num**      | Hold `Bksp`       | Number pad + operators                          |
| 5   | **Sym**      | Hold `Enter`      | Shifted symbols `{}[]()` etc.                   |
| 6   | **Fun**      | Hold `Del`        | F-keys, Print Screen, `studio_unlock`           |
| 7-9 | _(reserved)_ | --                | Extra layers available in ZMK Studio            |

### Bootloader access

`&bootloader` is on the top-row pinkie of every layer:

- **Left pinkie (pos 0):** Nav, Mouse, Media layers
- **Right pinkie (pos 9):** Num, Sym, Fun layers

---

## ZMK Studio

This firmware supports **[ZMK Studio](https://zmk.studio/)** -- a live keymap
editor that lets you remap keys without reflashing.

**To unlock Studio:** hold `Del` (right outer thumb) to enter the Fun layer,
then press `&studio_unlock` (right inner bottom row of Fun layer).

**Connection:**

- **USB:** plug in the left half, open [zmk.studio](https://zmk.studio/) in Chrome/Edge.
- **BLE (Linux only):** connect wirelessly via the Chrome/Edge web app or native Linux app.

> **Note:** Once you save changes in Studio, edits to `totem.keymap` won't apply
> until you do **"Restore Stock Settings"** in Studio.
> The 3 reserved layers (7-9) can be enabled and populated entirely within Studio.

---

## Repository structure

```
build.yaml                              # Build matrix for GitHub Actions
config/
  west.yml                              # ZMK source manifest (tracks main)
  boards/shields/totem/
    Kconfig.defconfig                   # Kconfig: name, split, sleep, battery, mouse, studio
    Kconfig.shield                      # Shield detection
    totem.zmk.yml                       # Shield metadata (features: keys, studio)
    totem.dtsi                          # Matrix transform + physical layout (ZMK Studio)
    totem.keymap                        # Miryoku QWERTY (Vi) keymap
    totem_left.overlay                  # Left half GPIO pins
    totem_right.overlay                 # Right half GPIO pins (mirrored)
.github/workflows/build.yml            # CI: builds firmware on every push
```

---

## Flashing firmware

1. Push your changes -- GitHub Actions builds firmware automatically.
2. Go to the **Actions** tab and download the latest `firmware.zip`.
3. **Left half:** double-press reset, drag `totem_left-xiao_ble-zmk.uf2` onto the drive.
4. **Right half:** double-press reset, drag `totem_right-xiao_ble-zmk.uf2` onto the drive.
5. Flash `settings_reset-xiao_ble-zmk.uf2` to both halves to clear BLE bonds if needed.

## Useful links

- [ZMK docs](https://zmk.dev/docs)
- [ZMK keycodes](https://zmk.dev/docs/codes)
- [Miryoku reference](https://github.com/manna-harbour/miryoku/tree/master/docs/reference)
- [ZMK Studio](https://zmk.studio/)
- [TOTEM hardware](https://github.com/GEIGEIGEIST/totem)
