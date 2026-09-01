# Changelog

All notable changes to avocado-bsp-rubikpi3 are documented in this file.
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.1.1]

### Added
- Module set for the upstream-kernel BSP: the 20 modules the 6.18 defconfig
  builds as modules (msm/dispcc/gpucc display and GPU, lontium-lt9611, the
  Geni I2C and Snps femto PHY, the LPG/SPMI PMIC drivers, and the q6 audio DSP
  stack), plus `systemd-rubikpi3-masks`.

### Fixed
- `ext install` no longer fails on the 2026 feed. Ten packages that exist only
  in the downstream 6.6 kernel are now scoped with `kernel-6.6.*`, and the
  6.18 set is scoped with `kernel-6.18.*`, so each feed installs the list it
  actually has. The previous flat list was captured from an HWE-era `lsmod`,
  which cannot show a block the downstream defconfig had built in.

## [0.1.0]

### Added
- Initial release: Board support for the Thundercomm RUBIK Pi 3 (QCS6490).
- CI via the shared `avocado-linux/actions` reusable workflows: PR build check
  (`test.yml`) and tag-driven package + publish to the Avocado feed (`release.yml`).
