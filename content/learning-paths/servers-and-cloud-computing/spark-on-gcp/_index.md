---
title: Deploy Apache Spark on Google Axion

minutes_to_complete: 60

who_is_this_for: This introductory topic is for software developers interested in migrating their Apache Spark workloads from x86_64 platforms to Arm-based platforms, specifically on Google Axion–based C4A virtual machines.  

learning_objectives:
  - Start an Arm virtual machine on Google Cloud Platform (GCP) using the C4A Google Axion instance family, with RHEL 9 as the base image.
  - Install and configure Apache Spark on an Arm-based GCP C4A instance.
  - Validate Spark functionality through baseline testing.
  - Benchmark Apache Spark performance on Arm.

prerequisites:
  - A [Google Cloud Platform (GCP)](https://cloud.google.com/free?utm_source=google&hl=en) account with billing enabled
  - Familiarity with distributed computing concepts and the [Apache Spark architecture](https://spark.apache.org/docs/latest/)

# START generated_summary_faq
generated_summary_faq:
  template_version: summary-faq-v3
  generated_at: '2026-11-25T17:32:03Z'
  generator: ai
  ai_assisted: true
  ai_review_required: true
  model: gpt-5
  prompt_template: summary-faq-v3
  source_hash: e83c6550dbc325511d5fea01186dffc1a6d0a68f49bd4a91cf19f87ddfa75dfc
  summary_generated_at: '2026-11-25T17:32:03Z'
  summary_source_hash: e83c6550dbc325511d5fea01186dffc1a6d0a68f49bd4a91cf19f87ddfa75dfc
  faq_generated_at: '2026-11-25T17:32:03Z'
  faq_source_hash: e83c6550dbc325511d5fea01186dffc1a6d0a68f49bd4a91cf19f87ddfa75dfc
  summary: >-
    You'll deploy Apache Spark on a Google Axion C4A VM and validate it with a Scala job. First,
    you'll create a C4A instance with a RHEL 9 Arm image. You'll then install
    Java, Maven, and Spark, and run a baseline job that prints squared values. Finally, you'll
    run Spark SQL micro-benchmarks and examine the reported metrics.
  faqs:
  - question: Which VM options should I choose when creating the instance?
    answer: >-
      Select the `C4A` series and a machine type such as `c4a-standard-4`. For the operating system,
      choose the Arm image variant of Red Hat Enterprise Linux 9.
  - question: How do I verify Spark before running the baseline test?
    answer: >-
      Apply the shell configuration with `source ~/.bashrc`, then run `spark-shell --version`. You should see a version number in the output.
  - question: How do I know Spark installed correctly before running benchmarks?
    answer: >-
      Run the baseline Scala job in `spark-shell`. You should see `Squared values: 1, 4, 9,
      16, 25`, which confirms that the job ran in local mode.
  - question: Where do the Spark benchmarks come from, and what result should I expect?
    answer: >-
      You run SQL micro-benchmarks from the Apache Spark source tree with the SBT-based
      framework. The output of the benchmarks includes metrics that you can compare across runs.
  - question: Which metrics should I use to compare the benchmark results?
    answer: >-
      Use **Best Time (ms)** for the fastest run, **Avg Time (ms)** for the average, and **Stdev (ms)**
      to judge variation. **Rate (M/s)** shows how many million rows you process per second.
# END generated_summary_faq

author: Pareena Verma

generate_summary_faq: false
rerun_summary: false
rerun_faqs: false

##### Tags
skilllevels: Advanced
subjects: Performance and Architecture
platforms:
  - Google Axion

armips:
  - Neoverse

tools_software_languages:
  - Apache Spark
  - Python

operatingsystems:
  - Linux

# ================================================================================
#       FIXED, DO NOT MODIFY
# ================================================================================
further_reading:
  - resource:
      title: Google Cloud official documentation
      link: https://cloud.google.com/docs
      type: documentation

  - resource:
      title: Apache Spark documentation
      link: https://spark.apache.org/
      type: documentation

  - resource:
      title: Scala programming language official website
      link: https://scala-lang.org
      type: website

weight: 1                       # _index.md always has weight of 1 to order correctly
layout: "learningpathall"       # All files under learning paths have this same wrapper
learning_path_main_page: "yes"  # Indicates this should be surfaced when looking for related content. Only set for _index.md of learning path content.
---

