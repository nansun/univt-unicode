# CHANGES

### 2020.12.31 / 5.11-rc1

- Resync for linux-5.11.y
- Update font data to GNU Unifont 13.0.05

## 2020.12.14 / 5.10

- Resync for linux-5.10.y
- Update font data to GNU Unifont 13.0.04
- Workaround for some Chinese punctuation marks
- Fix crash when rotating with different font size
- Fix line wrap for double width characters
- Workaround from [Gentoo-zh/linux-cjktty@6caf83a](https://github.com/Gentoo-zh/linux-cjktty/commit/6caf83a638886220d1e1880c92e8b18243c3965a)
- Support `32x32` font for high resolution screens (experimental, make sure the font data patch is applied)

## 2020.11.17 / 5.9.8

- Resync for linux-5.9.8
- Update font data to GNU Unifont 13.0.03

## 2020.11.16 / 5.9

- Base on [AOSC univt](https://github.com/AOSC-Dev/aosc-os-abbs)
- Resync for linux-5.9.y
- Remove soft scrollback code support (upstream)
  - [torvalds/linux@5014547](https://github.com/torvalds/linux/commit/50145474f6ef4a9c19205b173da6264a644c7489)
