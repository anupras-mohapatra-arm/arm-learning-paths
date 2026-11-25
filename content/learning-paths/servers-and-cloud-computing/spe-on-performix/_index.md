---
title: Enable Arm SPE for Performix memory access analysis

description: Learn how to verify and enable Arm Statistical Profiling Extension (SPE) on Arm Linux machines, including systems hosted through cloud service providers, so the Memory Access recipe in Arm Performix can run on supported environments.

minutes_to_complete: 30

who_is_this_for: This is an introductory topic for software developers and performance engineers who want to prepare Arm Linux machines, including cloud-hosted systems, for Arm Performix memory access profiling.

learning_objectives:
    - Check whether Arm Statistical Profiling Extension (SPE) is already available on an Arm Linux system using Sysreport and kernel-level checks.
    - Identify the hardware, platform, and kernel requirements that allow Linux to expose the SPE driver.
    - Apply Linux-side changes such as loading the SPE PMU module, installing matching kernel modules, or selecting an OS or kernel with SPE support.
    - Identify when a cloud instance doesn't expose SPE to the guest OS, and choose a suitable system for Arm Performix memory access analysis.

prerequisites:
    - Access to a Linux-based Arm bare-metal system with sudo or root access, such as an Arm AGI CPU platform that exposes SPE
    - Access to [Arm Performix](/install-guides/performix/) on your host machine, and SSH access to the target system
    - Familiarity with the Linux command line and SSH

# START generated_summary_faq
generated_summary_faq:
  template_version: summary-faq-v3
  generated_at: '2026-11-25T17:33:33Z'
  generator: ai
  ai_assisted: true
  ai_review_required: true
  model: gpt-5
  prompt_template: summary-faq-v3
  source_hash: d9e33e797eb45bbfe79e1dbb701091b4292a3946f22c4831a053631ef67bdfbc
  summary_generated_at: '2026-11-25T17:33:33Z'
  summary_source_hash: d9e33e797eb45bbfe79e1dbb701091b4292a3946f22c4831a053631ef67bdfbc
  faq_generated_at: '2026-11-25T17:33:33Z'
  faq_source_hash: d9e33e797eb45bbfe79e1dbb701091b4292a3946f22c4831a053631ef67bdfbc
  summary: >-
    You'll check and enable Arm SPE on an Arm Linux target for
    Performix memory access analysis. First, you'll check the Performix precheck and inspect kernel
    and driver support. If needed, you'll install matching kernel extra modules and load
    `arm_spe_pmu`. You'll then verify `perf sampling: SPE` with Sysreport or consider another
    operating system, kernel, or bare-metal system when SPE remains unavailable.
  faqs:
  - question: How do I know if SPE is already enabled on my system?
    answer: >-
      Check the running kernel and whether the `arm_spe_pmu` driver is built in or loaded.
      Then, run Sysreport and look for `perf sampling: SPE`.
  - question: What should I do if the arm_spe_pmu module isn't on my machine?
    answer: >-
      Search for a kernel extra-modules package matching your running kernel. If you find one,
      install it, load `arm_spe_pmu`, and verify Statistical Profiling Extension (SPE) with Sysreport. If the kernel lacks SPE
      support, consider another operating system or kernel.
  - question: What should I check if I'm on a cloud virtual machine and can't access SPE?
    answer: >-
      Check whether your cloud platform exposes SPE to the guest OS. If it doesn't, you can
      use a bare-metal instance or another Arm system that exposes SPE.
  - question: If my kernel doesn’t expose SPE, should I rebuild it or switch OS first?
    answer: >-
      Try another operating system or kernel image with SPE support first. You can rebuild
      your current kernel if you specifically need that configuration.
  - question: What should I confirm before running the Performix Memory Access recipe?
    answer: >-
      Confirm that Sysreport shows `perf sampling: SPE` and that the Performix **Memory Access**
      recipe reports **All checks passing!**. You also need SSH access from the Performix host
      to the target.
# END generated_summary_faq

author: Kieran Hejmadi

generate_summary_faq: false
rerun_summary: false
rerun_faqs: false

### Tags
skilllevels: Introductory
subjects: Performance and Architecture
platforms:
    - Arm AGI CPU
    - AWS Graviton
    - Google Axion
    - Microsoft Azure Cobalt
armips:
    - Neoverse
tools_software_languages:
    - Arm Performix
    - Sysreport
    - Linux kernel
    - perf
operatingsystems:
    - Linux

further_reading:
    - resource:
        title: Arm Performix install guide
        link: https://learn.arm.com/install-guides/performix/
        type: documentation
    - resource:
        title: Arm Statistical Profiling Extension documentation
        link: https://developer.arm.com/documentation/100616/0401/?lang=en
        type: documentation
    - resource:
        title: Arm Performix
        link: https://developer.arm.com/servers-and-cloud-computing/arm-performix
        type: website
    - resource:
        title: Get ready for performance analysis with Sysreport
        link: https://learn.arm.com/learning-paths/servers-and-cloud-computing/sysreport/
        type: documentation
    - resource:
        title: Analyze cache behavior with Perf C2C on Arm
        link: https://learn.arm.com/learning-paths/servers-and-cloud-computing/false-sharing-arm-spe/
        type: learning-path

### FIXED, DO NOT MODIFY
# ================================================================================
weight: 1                       # _index.md always has weight of 1 to order correctly
layout: "learningpathall"       # All files under learning paths have this same wrapper
learning_path_main_page: "yes"  # This should be surfaced when looking for related content. Only set for _index.md of learning path content.
---
