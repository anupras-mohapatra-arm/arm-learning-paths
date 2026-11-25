---
title: Learn the Arm Neoverse N1 performance analysis methodology

minutes_to_complete: 60

who_is_this_for: This is an introductory topic for software developers who want to learn about performance analysis methodology for Linux applications running on Arm Neoverse. The Learning Path was tested on the `a1.metal` instance type.

learning_objectives:
    - Identify sampling and counting for performance analysis.
    - Determine commonly used hardware metrics.
    - Analyze a sample application using the Arm Telemetry Solution and Linux Perf.
    - Make an application code change and see improved performance.

prerequisites:
    - An Arm Neoverse N1 computer running Linux, with a bare metal or cloud metal instance recommended because they expose more counters 
    - An installation of [Arm Telemetry Solution](/install-guides/topdown-tool/)

# START generated_summary_faq
generated_summary_faq:
  template_version: summary-faq-v3
  generated_at: '2026-11-25T17:38:45Z'
  generator: ai
  ai_assisted: true
  ai_review_required: true
  model: gpt-5
  prompt_template: summary-faq-v3
  source_hash: 6ea3b7e067d73012706a602881f8c805cbd1a259247358216ac8231a3a35b4b6
  summary_generated_at: '2026-11-25T17:38:45Z'
  summary_source_hash: 6ea3b7e067d73012706a602881f8c805cbd1a259247358216ac8231a3a35b4b6
  faq_generated_at: '2026-11-25T17:38:45Z'
  faq_source_hash: 6ea3b7e067d73012706a602881f8c805cbd1a259247358216ac8231a3a35b4b6
  summary: >-
    You'll analyze an Arm Neoverse N1 workload with the Arm Telemetry Solution and Linux `perf`. You'll
    then compare a software prefetch change with the baseline. First, you'll review performance
    events and build the DynamoRIO stride benchmark. You'll collect counting and sampling metrics
    to locate possible bottlenecks. Finally, you'll rebuild the benchmark with prefetch enabled
    and compare its instruction, cycle, runtime, and IPC results.
  faqs:
  - question: What do I need before collecting performance metrics?
    answer: >-
      Install [Arm Telemetry Solution](/install-guides/topdown-tool/) before you
      collect metrics. You also need the GNU C++ compiler, `g++`, to build the benchmark.
  - question: What should I do if I'm running the application on a VM and some counters are missing?
    answer: >-
      You might see fewer available counters on a VM. Use the metrics that your system exposes. Alternatively,
      use a bare metal or cloud metal Neoverse N1 system for broader counter access.
  - question: My results don’t match the white paper. Is that expected?
    answer: >-
      Yes. You might get different counts because the the Neoverse N1 Software
      Development Platform was used in the white paper. Your hardware might differ from that platform.
  - question: How do I enable and tune software prefetch in the benchmark?
    answer: >-
      Rebuild `stride.cpp` with `g++ -g -O3 -DENABLE_PREFETCH -DDIST=100 stride.cpp -o stride`. You can change `DIST` and compare the measurements. 
  - question: What should I capture to compare baseline and modified runs?
    answer: >-
      Compare your baseline and prefetched `perf` counts for instructions and cycles, plus IPC
      and runtime. Note the `DIST` value that you used so that you can relate the results to the build.
# END generated_summary_faq

author: Jason Andrews

generate_summary_faq: false
rerun_summary: false
rerun_faqs: false

### Tags
skilllevels: Introductory
subjects: Performance and Architecture
armips:
    - Neoverse
tools_software_languages:
    - perf
    - Telemetry
    - Runbook

operatingsystems:
    - Linux

further_reading:
    - resource:
        title: "Arm Neoverse N1: Core Performance Analysis Methodology"
        link: https://armkeil.blob.core.windows.net/developer/Files/pdf/white-paper/neoverse-n1-core-performance-v2.pdf
        type: documentation
    - resource:
        title: "Arm Neoverse N1 PMU Guide"
        link: https://developer.arm.com/documentation/PJDOC-466751330-547673/r4p1/ 
        type: documentation
    - resource:
        title: "Introduction to Computer Architecture"
        link: https://www.arm.com/resources/education/education-kits/computer-architecture 
        type: book
    - resource:
        title: "Computer Architecture: A Quantitative Approach"
        link: https://www.amazon.com/Computer-Architecture-Quantitative-John-Hennessy/dp/012383872X
        type: documentation

### FIXED, DO NOT MODIFY
# ================================================================================
weight: 1                       # _index.md always has weight of 1 to order correctly
layout: "learningpathall"       # All files under learning paths have this same wrapper
learning_path_main_page: "yes"  # This should be surfaced when looking for related content. Only set for _index.md of learning path content.
---

