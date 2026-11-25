---
title: Port code to Arm Scalable Vector Extension 

minutes_to_complete: 30   

who_is_this_for: This is an introductory topic for software developers using SIMD instructions for high-performance computing, machine learning, digital signal processing, and audio and video codec applications.

learning_objectives: 
    - Identify the differences between Scalable Vector Extension (SVE) and Neon for vectorization.
    - Compile code for SVE-capable Arm processors.
    - Run SVE instructions on any Armv8-A processor.

prerequisites:
    - General knowledge about SIMD processing, vectorization or Arm Neon
    - An Arm computer running Linux, such as a cloud instance or an Arm AGI CPU platform

# START generated_summary_faq
generated_summary_faq:
  template_version: summary-faq-v3
  generated_at: '2026-11-25T17:34:41Z'
  generator: ai
  ai_assisted: true
  ai_review_required: true
  model: gpt-5
  prompt_template: summary-faq-v3
  source_hash: a5ec987958694569f0a6ee9126db58e8f23d245b3b0d0f3eba24f780760c5908
  summary_generated_at: '2026-11-25T17:34:41Z'
  summary_source_hash: a5ec987958694569f0a6ee9126db58e8f23d245b3b0d0f3eba24f780760c5908
  faq_generated_at: '2026-11-25T17:34:41Z'
  faq_source_hash: a5ec987958694569f0a6ee9126db58e8f23d245b3b0d0f3eba24f780760c5908
  summary: >-
    You'll compile and run code for Arm SVE on Linux. First, you'll
    compare SVE with Arm Neon and inspect an SVE vector-length example. You'll then compile C
    and Fortran with GNU or Arm toolchains and review the generated instructions. Finally,
    you'll run an SVE example with QEMU. If your system lacks SVE support, you'll use Arm Instruction Emulator.
  faqs:
  - question: Which GCC options should I use to enable or disable SVE autovectorization?
    answer: >-
      Compile with `-march=armv8-a+sve`. Enable GCC autovectorization with `-O3`
      or `-ftree-vectorize`, and disable it with `-fno-tree-vectorize`.
  - question: How do I know if the compiler emitted SVE instructions instead of Neon?
    answer: >-
      Compare the generated disassembly with and without `-march=armv8-a+sve`. Look
      for Scalable Vector Extension (SVE) instructions such as `whilelo` and `ld1d`.
  - question: How do I complete the Learning Path if my hardware doesn't support SVE?
    answer: >-
      You can use QEMU or Arm Instruction Emulator (ArmIE) to complete the Learning Path without SVE
      hardware.
  - question: What should I keep in mind when moving from Neon to SVE?
    answer: >-
      Moving from Neon to SVE involves moving from fixed 128-bit registers to scalable vector length. Check
      the vector length on your target when you investigate SVE performance.
  - question: How can I count SVE instructions when running with ArmIE?
    answer: >-
     Run the example with the ArmIE `libinscount_emulated.so` plugin to count
      emulated instructions. Set the vector length with `-msve-vector-bits`, then compare
      the counts at different vector lengths.
# END generated_summary_faq

author: Florent Lebeau

generate_summary_faq: false
rerun_summary: false
rerun_faqs: false

### Tags
skilllevels: Introductory
subjects: AI/ML
platforms:
  - Arm AGI CPU
  - AWS Graviton
  - Microsoft Azure Cobalt
  - Google Axion
  - Oracle Cloud Infrastructure (OCI) Ampere Compute
armips:
    - Neoverse
    - Cortex-A
operatingsystems:
    - Linux
tools_software_languages:
    - SVE
    - Neon
    - armie
    - GCC
    - armclang
    - Runbook

further_reading:
    - resource:
        title: Introduction to SVE
        link: https://developer.arm.com/documentation/102476/latest/
        type: website
    - resource:
        title: SVE Optimization Guide
        link: https://developer.arm.com/documentation/102699/0100/?lang=en
        type: documentation
    - resource:
        title: Tutorials - Introduction to SVE2
        link: https://developer.arm.com/documentation/102340/0001/?lang=en
        type: documentation
    - resource:
        title: Arm Instruction Emulator user guide
        link: https://developer.arm.com/documentation/102190/22-0/Get-started/Get-started-with-Arm-Instruction-Emulator
        type: documentation
    - resource:
        title: Accelerating DSP functions with dot product instructions
        link: https://developer.arm.com/documentation/102651/a/?lang=en
        type: documentation
    - resource:
        title: Optimizing HPCG for Arm SVE
        link: https://developer.arm.com/community/arm-community-blogs/b/servers-and-cloud-computing-blog/posts/optimizing-hpcg-for-arm-sve
        type: blog

### FIXED, DO NOT MODIFY
# ================================================================================
weight: 1                       # _index.md always has weight of 1 to order correctly
layout: "learningpathall"       # All files under learning paths have this same wrapper
learning_path_main_page: "yes"  # This should be surfaced when looking for related content. Only set for _index.md of learning path content.
---

