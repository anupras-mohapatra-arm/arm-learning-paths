---
title: Get ready for performance analysis with Sysreport

minutes_to_complete: 10

who_is_this_for: This is an introductory topic for software developers who want to use the system capability reporting tool, Sysreport, to understand and configure the performance features of their Arm Linux system.

learning_objectives: 
    - Run Sysreport to get a quick report of the system configuration.
    - Discover which performance analysis features are available and enabled. 
    - Make configuration changes to improve performance information collection.

prerequisites:
    - An Arm-based system (bare metal server, cloud instance, developer board) running Linux

# START generated_summary_faq
generated_summary_faq:
  template_version: summary-faq-v3
  generated_at: '2026-11-25T17:36:03Z'
  generator: ai
  ai_assisted: true
  ai_review_required: true
  model: gpt-5
  prompt_template: summary-faq-v3
  source_hash: 3cbbe4de333aebc03ddcce363eef30db7829f8f2e7baf3f952e01847ae24f59f
  summary_generated_at: '2026-11-25T17:36:03Z'
  summary_source_hash: 3cbbe4de333aebc03ddcce363eef30db7829f8f2e7baf3f952e01847ae24f59f
  faq_generated_at: '2026-11-25T17:36:03Z'
  faq_source_hash: 3cbbe4de333aebc03ddcce363eef30db7829f8f2e7baf3f952e01847ae24f59f
  summary: >-
    You'll use Sysreport to assess whether an Arm Linux system is ready for performance analysis.
    First, you'll check Python and Git, clone the Sysreport repository, and test the tool. You'll
    then run it to view hardware, operating system, and performance feature details. Finally,
    you'll interpret its advice and adjust `kernel.perf_event_paranoid` before
    checking the report again.
  faqs:
  - question: What result should I expect after running Sysreport?
    answer: >-
     You'll see an on-screen report of system hardware, operating system configuration, and
      performance features. By default, the report includes advice about possible configuration changes.
  - question: How do I know if the current system has the performance features that I need?
    answer: >-
      Check **Performance features** in the Sysreport output for the capabilities that you need.
      You can also read the suggested actions for configuration changes.
  - question: What should I do if the report shows that a needed feature is missing or disabled?
    answer: >-
      Adjust the configuration or choose a system with the feature. For example, you can set `kernel.perf_event_paranoid=0` and run Sysreport again when
      non-privileged users can't monitor system-level events.
  - question: How do I confirm that Sysreport is ready to run?
    answer: >-
      From the `sysreport/src` directory of the cloned directory, run
      `python3 sysreport.py --help`. You should see the usage message and available options.
  - question: Can I run Sysreport without configuration advice?
    answer: >-
      You can add `--no-advice` when you run Sysreport to hide its suggested configuration
      changes while viewing the system report.
# END generated_summary_faq

author: James Whitaker

generate_summary_faq: false
rerun_summary: false
rerun_faqs: false

### Tags
skilllevels: Introductory
subjects: Performance and Architecture
platforms:
  - AWS Graviton
  - Microsoft Azure Cobalt
  - Google Axion
  - Oracle Cloud Infrastructure (OCI) Ampere Compute
armips:
    - Cortex-A 
    - Neoverse
tools_software_languages:
    - Python
    - Runbook

operatingsystems:
    - Linux

further_reading:
    - resource:
        title: Perf for Linux on Arm (LinuxPerf)
        link: /install-guides/perf/
        type: website
    - resource:
        title: APerf 
        link: /install-guides/aperf/
        type: website
    - resource:
        title: Arm Performance Studio
        link: /install-guides/ams/
        type: website

### FIXED, DO NOT MODIFY
# ================================================================================
weight: 1                       # _index.md always has weight of 1 to order correctly
layout: "learningpathall"       # All files under learning paths have this same wrapper
learning_path_main_page: "yes"  # This should be surfaced when looking for related content. Only set for _index.md of learning path content.
---

