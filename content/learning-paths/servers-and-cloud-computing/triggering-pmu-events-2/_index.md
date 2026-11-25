---
title: Explore Neoverse non-cache PMU events with C and assembly

minutes_to_complete: 30

who_is_this_for: This is an advanced topic for software and hardware engineers to learn about why common non-cache Performance Monitor Unit (PMU) events occur.

learning_objectives: 
    - Identify common non-cache PMU events.
    - Identify why specific code triggers specific PMU events on the Neoverse N2 Core.

prerequisites:
    - Some familiarity with performance analysis
    - The ability to read Arm assembly code

# START generated_summary_faq
generated_summary_faq:
  template_version: summary-faq-v3
  generated_at: '2026-11-25T17:40:36Z'
  generator: ai
  ai_assisted: true
  ai_review_required: true
  model: gpt-5
  prompt_template: summary-faq-v3
  source_hash: c72a91d640e7f4a5e189459bdd9f0f36f17454e354a557219fd9ddf0592f330c
  summary_generated_at: '2026-11-25T17:40:36Z'
  summary_source_hash: c72a91d640e7f4a5e189459bdd9f0f36f17454e354a557219fd9ddf0592f330c
  faq_generated_at: '2026-11-25T17:40:36Z'
  faq_source_hash: c72a91d640e7f4a5e189459bdd9f0f36f17454e354a557219fd9ddf0592f330c
  summary: >-
    You'll examine non-cache PMU events on an Arm Neoverse N2 core using C and A64 assembly
    examples. First, you'll interpret Topdown L1 metrics for backend stalls, frontend stalls,
    speculation, and retiring. You'll then compare instruction TLB counts before and after a TLB
    clear. Finally, you'll inspect operation mix counts for
    Neon and floating point, as well as integer, branch, load, and store activity.
  faqs:
  - question: Do I need console output to complete the Learning Path?
    answer: >-
      Yes. You need an environment that can print the PMU counts, for example with `printf`. You can then
      compare the counts with the examples.
  - question: How do I know that the ITLB walk test initiated a walk?
    answer: >-
      Check the output after `TLBI ALLE3` clears the TLB. You should see `ITLB_WALK` and
      `L1I_TLB_REFILL` at `3` in the example. Before the clear, the self-modifying code
      reports `ITLB_WALK` at `0`.
  - question: What result should I expect from the SIMD (Neon) example?
    answer: >-
      Compare your counts with `INST_SPEC` at `12`, `ASE_SPEC` at `1`, and `ASE_INST_SPEC`
      at `3` in the Neon example.
  - question: Is event counts variation between runs expected on Linux?
    answer: >-
      Yes. You can see different counts because Linux adds operating system activity to the
      bare-metal example workload.
  - question: Which reference should I use to interpret the PMU events?
    answer: >-
      You can use the
      [Arm Neoverse N2 PMU guide](https://developer.arm.com/documentation/PJDOC-466751330-590448/2-0/?lang=en)
      to interpret the event definitions that are shown in the Learning Path.
# END generated_summary_faq

author: Johanna Skinnider

generate_summary_faq: false
rerun_summary: false
rerun_faqs: false

### Tags
skilllevels: Advanced
subjects: Performance and Architecture
operatingsystems:
    - Linux
armips:
    - Neoverse
tools_software_languages:
    - C
    - Assembly
    - Runbook

further_reading:
    - resource:
        title: Arm Neoverse N2 PMU Guide
        link: https://developer.arm.com/documentation/PJDOC-466751330-590448/2-0/?lang=en
        type: documentation
    - resource:
        title: Arm CPU Telemetry Solution Topdown Methodology Specification 
        link: https://developer.arm.com/documentation/109542/0100/?lang=en
        type: documentation
    - resource:
        title: Arm Neoverse N2 Core Telemetry Specification 
        link: https://developer.arm.com/documentation/109215/0200/?lang=en
        type: documentation

### FIXED, DO NOT MODIFY
# ================================================================================
weight: 1                       # _index.md always has weight of 1 to order correctly
layout: "learningpathall"       # All files under learning paths have this same wrapper
learning_path_main_page: "yes"  # This should be surfaced when looking for related content. Only set for _index.md of learning path content.
---

