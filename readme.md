# EmuX — Deterministic CPU Emulator for Yocto, QEMU, CI, ARM64

## Project Overview: 
This project is a user‑space **8086 emulator** that runs inside a Yocto‑built Linux image and is validated in QEMU. The emulator will include an instruction decoder, memory model, I/O hooks, a deterministic regression test suite, and a systemd service so the emulator runs automatically on boot. The goal is to demonstrate low‑level systems engineering: cross‑compilation, deterministic testing, performance profiling, and Yocto integration.

## Target Build System
- **Yocto** is the chosen build system to customize and streamline the build for Raspberry Pi 3 B+.

## Hardware Platform
**Platform**:  Raspberry Pi 3 B+ (Cortex‑A53, ARMv8 capable). 
Pi 3 B+ gives a good balance of CPU performance, community BSP support (meta‑raspberrypi), and low cost for an emulator project.  Development and CI will use Yocto images run in QEMU for fast iteration; final validation will be performed on a physical Pi 3 B+ that I will source myself. The Yocto layer meta-myemu will depend on meta-raspberrypi for kernel, firmware, and DTBs. MACHINE used for builds: raspberrypi3.

## Open Source Projects
1. **Yocto Project / meta‑raspberrypi** - reproducible SD images and kernel/DTB for Pi 3.
2. **QEMU** - run and validate images in CI; reproduce ARM runtime behavior.
3. **GCC / binutils cross toolchains** - cross‑compile emulator for aarch64 and armhf.

## Previously Discussed Content
- **Yocto**: Covered in yocto bringup assignment 6.
- Creating standalone linux distribution with Yocto that links to git repositories.
- Including the Yocto build scripts to apply patches for bblayer.conf and local.conf file before bitbake execution.

## New Content
- Correct instruction decoder and CPU core (NES or 8086) with a faithful memory model and exception/interrupt semantics.
- The implementation with sanitizer‑backed unit tests and a deterministic regression suite to ensure correctness.
- Validation by booting Yocto images in QEMU from CI, running the regression suite on each build.
- Package everything as a Yocto recipe and systemd service so the emulator boots reproducibly on a Raspberry Pi 3 B+.

## Source Code Organization
- **Yocto Build System Repository**: [final-project-sana-all](https://github.com/cu-ecen-aeld/final-project-sana-all)

## Team Members
Mcrey Fonacier - Full implementation (Yocto, drivers, application, integration)

## Schedule
[Link to Schedule Page](https://github.com/users/sana-all/projects/3/views/1)

## Demo Video Links
*The links are yet to be decided as of now.*

- **Mcrey Fonacier**: *[link]*  
