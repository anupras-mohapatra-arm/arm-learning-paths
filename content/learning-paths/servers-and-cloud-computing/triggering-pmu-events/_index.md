---
title: Explore Neoverse cache PMU events using C and assembly language

minutes_to_complete: 30

who_is_this_for: This is an advanced topic for software and hardware engineers who want to learn about the causes of common Neoverse cache Performance Monitor Unit (PMU) events.

learning_objectives: 
    - Identify common cache PMU events.
    - Identify why some code triggers PMU events on the Neoverse N2 core.
    - Identify the events triggered during common scenarios.

prerequisites:
    - Knowledge of performance analysis
    - The ability to read Arm assembly code

# START generated_summary_faq
generated_summary_faq:
  template_version: summary-faq-v3
  generated_at: '2026-11-25T17:40:02Z'
  generator: ai
  ai_assisted: true
  ai_review_required: true
  model: gpt-5
  prompt_template: summary-faq-v3
  source_hash: 6bc7673fcfcb511c247a8323461cd9ad3b42fa3dc076c1eface5d77fdc7d2da7
  summary_generated_at: '2026-11-25T17:40:02Z'
  summary_source_hash: 6bc7673fcfcb511c247a8323461cd9ad3b42fa3dc076c1eface5d77fdc7d2da7
  faq_generated_at: '2026-11-25T17:40:02Z'
  faq_source_hash: 6bc7673fcfcb511c247a8323461cd9ad3b42fa3dc076c1eface5d77fdc7d2da7
  summary: >-
    You'll examine how C and assembly examples affect cache PMU events on an Arm Neoverse N2 core.
    First, you'll review the PMU and investigate L1 data cache counts from reads and stores. You'll
    then examine separate instruction cache examples, followed by L2 read and write events.
    Finally, you'll compare last-level cache read and miss counts, and relate the reported values
    to the example memory system.
  faqs:
  - question: What result should I expect after running the L1 D-cache store loop?
    answer: >-
      Compare your counts with the example `L1D_CACHE`, `L1D_CACHE_REFILL`, and
      `INST_RETIRED` values. You should see accesses exceed refills.
  - question: What should I check if the L2 cache events don't increase?
    answer: >-
      Check whether your stores to Normal Cacheable memory fill the L1 data cache. 
  - question: How do I interpret the LL cache read and miss events?
    answer: >-
      In the standalone N2 example, you see `LL_CACHE_RD` at `0` and `LL_CACHE_MISS_RD` at
      `326`. This is because the example system has no cache level after L2. The nonzero
      miss count likely reflects external bus reads.
  - question: Where can I find definitions for the PMU events used in the Learning Path?
    answer: >-
      You can find the event definitions in the
      [Arm Neoverse N2 PMU guide](https://developer.arm.com/documentation/PJDOC-466751330-590448/2-0/?lang=en).
  - question: Do I need to use the exact memory addresses shown in the code examples?
    answer: >-
      You need access to Normal Cacheable memory to reproduce the event categories in the
      examples. If you use different addresses, check their memory attributes before comparing
      counts.
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

