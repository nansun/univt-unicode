# CHANGES

## 20201214 / 5.10

- Resync for linux-5.10.y
- Update font data to GNU Unifont 13.0.04
- Workaround for some Chinese punctuation marks
- Fix crash when rotating with different font size
- Fix line wrap for double width characters
- Workaround from <https://github.com/Gentoo-zh/linux-cjktty/commit/6caf83a638886220d1e1880c92e8b18243c3965a>
- Support `32x32` font for high resolution screens (experimental, make sure the font data patch is applied)

## 20201117 / 5.9.8

- Resync for linux-5.9.8
- Update font data to GNU Unifont 13.0.03

## 20201116 / 5.9

- Base on [AOSC univt](https://github.com/AOSC-Dev/aosc-os-abbs)
- Resync for linux-5.9.y
- Remove soft scrollback code support (upstream)
