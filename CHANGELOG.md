# Changelog

All notable changes to avocado-bsp-rubikpi3 are documented in this file.
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.2.3]

### Added
- Adreno 643 GPU userspace on the 2026 feed: Turnip (`mesa-vulkan-drivers`)
  with the Vulkan loader (`vulkan-loader`), the Gallium DRI driver, GLES, EGL
  and GBM; and the a660 CP/GMU microcode (`linux-firmware-qcom-adreno-a660`),
  without which msm fails to load `a660_sqe.fw` and the GPU never boots.
- CDSP compute offload on the 2026 feed: `fastrpc` and `kernel-module-fastrpc`
  (`/dev/fastrpc`). Needs the Gunyah boot configuration, the provision default
  (`AVOCADO_HYPERVISOR=gunyah`); under KVM the CDSP stays offline on this board.
  Verified on RUBIK Pi 3 hardware 2026-09-19: the cdsp remoteproc boots and
  `/dev/fastrpc` appears. No inference workload has been run yet.

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
