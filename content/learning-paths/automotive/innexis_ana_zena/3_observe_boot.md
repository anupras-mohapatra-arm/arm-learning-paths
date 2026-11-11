---
title: Observe Zena CSS boot and inspect Linux
weight: 4

### FIXED, DO NOT MODIFY
layout: learningpathall
---

## Follow the boot handoff

Zena CSS exposes separate consoles for its Runtime Security Engine (RSE), Safety Island, and primary-compute software. Check each view before entering commands in the Linux guest.

Use the following sequence to connect the console views to the [Arm Zena CSS boot process](https://arm-zena-css.docs.arm.com/en/latest/design/boot_process.html):

1. The RSE starts first and prepares the Safety Island firmware and the Primary Compute boot image.
2. System Control Processor (SCP) firmware on the Safety Island starts and powers on the Primary Compute.
3. Trusted Firmware-A (TF-A) starts in the Primary Compute secure world. OP-TEE provides secure-world services, while U-Boot continues the normal-world boot.
4. U-Boot starts systemd-boot, which starts the Linux kernel and Edge Workload Abstraction and Orchestration Layer (EWAOL) userspace.

The Primary Compute Secure and Primary Compute views don't represent separate sets of CPUs. The secure-world software and Linux use the same application processor cores. This sequence describes the boot handoff. Console timestamps from different views aren't a single synchronized timeline.

## Inspect the boot consoles

In the Architecture Native Acceleration (ANA) **Serial Console** view, select each console for your virtual platform:

1. **RSE:** look for TF-M or RSE firmware messages.
2. **Safety Island:** look for an SCP firmware startup message.
3. **Primary Compute Secure:** look for TF-A or OP-TEE boot messages.
4. **Primary Compute:** wait for EWAOL Linux to finish booting.

![ANA Serial Console showing Safety Island firmware output and the console selector#center](ana_console_selector.png "Select a Zena CSS boot console")

The primary-compute console reaches a Linux login prompt. The other consoles show messages from different parts of the system. Don't expect the Linux shell on those views.

Record one identifying line from each console and the exact text of the Linux login prompt. If early firmware messages are no longer visible, record what's available. Don't infer that the stage didn't run. A firmware message doesn't replace a Linux boot check or prove that image authentication succeeded.

## Log in and inspect the guest

Use the login details supplied for your chamber and software image. The root account is used in the EWAOL example in the Siemens reference guide.

Run the following commands in the primary-compute Linux console:

```bash
cat /etc/os-release; uname -m; uname -r; grep -E '^(MemTotal|MemAvailable):' /proc/meminfo; df -h /
```

`uname -m` reports the Linux guest architecture, commonly `aarch64`. The other commands report the OS release of the guest, kernel, memory, and root-filesystem capacity. 

The Zena guest that the Learning Path was tested on returned the following values:

```output
ID=ewaol
NAME="Edge Workload Abstraction and Orchestration Layer"
VERSION="v2.1.0 (styhead)"
VERSION_ID=v2.1.0
VERSION_CODENAME="styhead"
PRETTY_NAME="Edge Workload Abstraction and Orchestration Layer v2.1.0 (styhead)"
CPE_NAME="cpe:/o:openembedded:ewaol:v2.1.0"
aarch64
6.6.54-yocto-standard
MemTotal:        8120232 kB
MemAvailable:    7857784 kB
Filesystem      Size  Used Avail Use% Mounted on
/dev/root        28G  1.3G   25G   5% /
```


## Check which CPUs Linux can use

In the same **Primary Compute** Linux console, inspect the CPUs present and online in this guest:

```bash
cat /sys/devices/system/cpu/present
cat /sys/devices/system/cpu/online
grep -c '^processor' /proc/cpuinfo
lscpu
```

The `present` file lists CPUs that Linux identifies as present. The `online` file lists CPUs available to the scheduler. The count from `/proc/cpuinfo` shows the processor entries in this Linux guest. It's not a count of every processing element in the Zena CSS vSoC.

The Zena Linux guest that the Learning Path was tested on returned the following values:

```output
0-15
0-15
16
Architecture:             aarch64
CPU(s):                   16
  On-line CPU(s) list:    0-15
  Model name:             Cortex-A720AE
  Core(s) per cluster:  16
  Cluster(s):           1
```
Your values can differ if your virtual platform uses another CPU configuration. 

Linux sees 16 online Cortex-A720AE CPUs in this example run. The Cortex-R82AE Safety Island and Cortex-M55 RSE run separate firmware and don't appear as extra Linux CPUs. The secure-world console also doesn't represent another set of CPUs. Compare the reported count with the CPU configuration selected for your virtual platform.

The cluster fields describe the topology presented to this Linux guest. They don't, by themselves, establish the internal cluster layout of the vSoC or the topology of a future physical device.

The configured DRAM of the vSoc and the RAM usable by its Linux image can differ. Compare the Linux-visible **MemTotal** with the project configuration when you document the environment.

If the login prompt doesn't appear, return to the primary-compute console and inspect its last boot messages. If a command is unavailable in your image, record the command and error. Use the available files under `/proc` to inspect the same property.

## What you've accomplished and what's next

You've inspected the Zena CSS boot on the ANA. 

Next, you'll use ANA port mapping to connect to this guest from your local computer.
