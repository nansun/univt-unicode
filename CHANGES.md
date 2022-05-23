# CHANGES

## 2022.05.23 / 5.18

- Resync for linux-5.18.y
- Fix build warnings with GCC 12 (`-Wbidi-chars=unpaired`)

## 2022.03.21 / 5.17

- Resync for linux-5.17.y
- Update font data to GNU Unifont 14.0.02
- Revert scroll acceleration code (upstream)
  - [torvalds/linux@1148836](https://github.com/torvalds/linux/commit/1148836fd3226c20de841084aba24184d4fbbe77)

## 2022.01.10 / 5.16

- Resync for linux-5.16.y
- Remove scroll acceleration code (upstream)
  - [torvalds/linux@b3ec8cd](https://github.com/torvalds/linux/commit/b3ec8cdf457e5e63d396fe1346cc788cf7c1b578)

## 2021.09.17 / 5.14.5

- Update font data to GNU Unifont 14.0.01

## 2021.02.22 / 5.11

- Resync for linux-5.11.y
- Update font data to GNU Unifont 13.0.06
- Reduce checkpatch.pl complaints

## 2020.12.14 / 5.10

- Resync for linux-5.10.y
- Update font data to GNU Unifont 13.0.04
- Workaround for some Chinese punctuation marks
- Fix crash when rotating with different font size
- Fix line wrap for double width characters
- Workaround from [Gentoo-zh/linux-cjktty@6caf83a](https://github.com/Gentoo-zh/linux-cjktty/commit/6caf83a638886220d1e1880c92e8b18243c3965a)
- Support 32x32 font for high resolution screens (experimental, make sure the font data patch is applied)

## 2020.11.17 / 5.9.8

- Resync for linux-5.9.8
- Update font data to GNU Unifont 13.0.03

## 2020.11.16 / 5.9

- Base on [AOSC univt](https://github.com/AOSC-Dev/aosc-os-abbs)
- Resync for linux-5.9.y
- Remove soft scrollback code (upstream)
  - [torvalds/linux@5014547](https://github.com/torvalds/linux/commit/50145474f6ef4a9c19205b173da6264a644c7489)
