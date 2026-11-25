---
title: Run Spark applications on Microsoft Azure Cobalt 100 processors

minutes_to_complete: 60

who_is_this_for: This is an advanced topic that introduces Spark deployment on Microsoft Azure Cobalt 100 (Arm-based) virtual machines. It is designed for developers migrating Spark applications from x86_64 to Arm.

learning_objectives: 
    - Provision an Azure Arm64 virtual machine (VM) using Azure console.
    - Create an Azure Linux 3.0 Docker container.
    - Deploy a Spark application inside an Azure Linux 3.0 Arm64-based Docker container or an Azure Linux 3.0 custom-image based Azure virtual machine.
    - Run a suite of Spark benchmarks to understand and evaluate performance on the Azure VM.

prerequisites:
    - A [Microsoft Azure](https://azure.microsoft.com/) account with access to Cobalt 100-based instances (Dpsv6)
    - A machine with [Docker](/install-guides/docker/) installed
    - Familiarity with distributed computing concepts and the [Apache Spark architecture](https://spark.apache.org/docs/latest/)

# START generated_summary_faq
generated_summary_faq:
  template_version: summary-faq-v3
  generated_at: '2026-11-25T17:31:29Z'
  generator: ai
  ai_assisted: true
  ai_review_required: true
  model: gpt-5
  prompt_template: summary-faq-v3
  source_hash: e9d4d638266aa8e5370a85a7048184f7acf8befef17d255ebf393ca7cbeeb21c
  summary_generated_at: '2026-11-25T17:31:29Z'
  summary_source_hash: e9d4d638266aa8e5370a85a7048184f7acf8befef17d255ebf393ca7cbeeb21c
  faq_generated_at: '2026-11-25T17:31:29Z'
  faq_source_hash: e9d4d638266aa8e5370a85a7048184f7acf8befef17d255ebf393ca7cbeeb21c
  summary: >-
    You'll deploy Apache Spark on a Microsoft Azure Arm64 VM and validate a PySpark
    workload. First, you'll create the VM. You'll then prepare Azure Linux 3.0 in a container or
    custom VM image and install Java, Python, and Spark. After setup, you'll run a DataFrame test that prints two
    rows. Finally, you'll run Spark benchmarks and compare the reported results.
  faqs:
  - question: How can I set up Azure Linux 3.0 for Spark?
    answer: >-
      You can run an Azure Linux 3.0 Docker container on the VM. Alternatively, you can create a VM from a custom
      Azure Linux 3.0 Arm64 image. Install Spark the same way in either
      environment.
  - question: How do I check that Java, Python, and Spark are installed?
    answer: >-
      Run `java -version` and `python3 --version` to check Java and Python. After installing
      Spark, run `spark-submit --version` and look for the Spark version in its output.
  - question: How do I run the PySpark functional test?
    answer: >-
      Create `test_spark.py` with the DataFrame example. Run
      `spark-submit test_spark.py` to display its two rows and stop the Spark session.
  - question: Which Spark benchmark do I run?
    answer: >-
      Check out Spark `v4.0.0` from its source repository, build with the `-Pbenchmarks`
      profile, and run `JoinBenchmark`. Compare the reported join times and other metrics
      across the Arm64 and x86_64 example tables.
  - question: What result should I expect from the functional test script?
    answer: >-
      You should see a DataFrame with `id` and `name` columns and two rows: `1, ARM64` and
      `2, Azure`. Spark should stop with exit code `0`.
# END generated_summary_faq

author: Pareena Verma

generate_summary_faq: false
rerun_summary: false
rerun_faqs: false

### Tags
skilllevels: Advanced
subjects: Performance and Architecture
platforms:
  - Microsoft Azure Cobalt

armips:
    - Neoverse

tools_software_languages:
    - Apache Spark
    - Python
    - Docker

operatingsystems:
    - Linux

further_reading:
  - resource:
      title: Azure Virtual Machines documentation
      link: https://learn.microsoft.com/en-us/azure/virtual-machines/
      type: documentation
  - resource:
      title: Azure Container Instances documentation
      link: https://learn.microsoft.com/en-us/azure/container-instances/
      type: documentation
  - resource:
      title: Docker overview
      link: https://docs.docker.com/get-started/overview/
      type: documentation
  - resource:
      title: Spark official website and documentation
      link: https://spark.apache.org/
      type: documentation
  - resource:
      title: Hadoop official website
      link: https://hadoop.apache.org/
      type: website

### FIXED, DO NOT MODIFY
# ================================================================================
weight: 1                       # _index.md always has weight of 1 to order correctly
layout: "learningpathall"       # All files under learning paths have this same wrapper
learning_path_main_page: "yes"  # This should be surfaced when looking for related content. Only set for _index.md of learning path content.
---

