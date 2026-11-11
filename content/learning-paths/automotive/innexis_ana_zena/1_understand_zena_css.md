---
title: Understand the Zena CSS virtual platform
weight: 2

### FIXED, DO NOT MODIFY
layout: learningpathall
---

## Understand the Zena CSS boot flow in Innexis ANA

In [Innexis Architecture Native Acceleration (ANA)](https://www.siemens.com/en-gb/products/ic/hav/innexis/architecture-native-acceleration/), a chamber provides the environment in which you can create and run a virtual platform. The Arm-Zena-CSS vSoC describes the virtual hardware. The [Arm-Zena-CSS Edge Workload Abstraction and Orchestration Layer (EWAOL) Software Stack](https://arm-zena-css.docs.arm.com/en/v2.2/overview.html) supplies the software images that are used to boot it.

The Learning Path was validated using Siemens Innexis ANA 2026.2. ANA menus, supplied assets, and software behavior might change in later releases. Use the ANA User Guide that matches your chamber version when a screen differs from the Learning Path.

Zena CSS has more than one processing area. You'll inspect the following consoles after starting the virtual platform:

| Console in ANA | What to look for |
| --- | --- |
| Runtime Security Engine (RSE) | Firmware messages associated with the Root of Security for the system. |
| Safety Island | SCP firmware messages from the Safety Island. |
| Primary Compute Secure | Secure-world and boot-stage messages for the primary-compute system. |
| Primary Compute | EWAOL Linux boot messages and the login prompt. |

The RSE starts the boot process on a Cortex-M55. It prepares firmware for the Cortex-R82AE Safety Island and the Primary Compute. SCP firmware on the Safety Island then powers on the Primary Compute.

Trusted Firmware-A (TF-A) and OP-TEE run in the Primary Compute secure world. U-Boot and systemd-boot lead to Linux in the normal world. The two Primary Compute console views show software running on the same Cortex-A720AE cores, not two separate groups of CPUs. For the reference software flow, see the [Arm Zena CSS boot process](https://arm-zena-css.docs.arm.com/en/latest/design/boot_process.html).

The firmware consoles help you see how the virtual system reaches Linux. They don't, by themselves, demonstrate that an application is secure or that a product has passed a security assessment.

For this Learning Path, your first working result is the EWAOL Linux login prompt on the primary-compute console. You'll then inspect the guest from its shell. You don't need to change firmware or rebuild the software stack.

Before continuing, locate **Arm-Zena-CSS** and its **EWAOL Software Stack** in your chamber. If either is absent, ask the chamber administrator which Zena assets are available.

## What you've learned and what's next

You've learned about the Innexis ANA consoles that you'll inspect and the Zena CSS boot flow.

Next, you'll create and start a Zena CSS virtual platform.
