---
title: Run Apache Spark SQL with Gluten and Velox on Azure Cobalt 100
description: Learn how to deploy, configure, and benchmark Apache Spark SQL on Azure Cobalt 100 Arm64 VMs using the Gluten plugin and Velox backend for native query acceleration, with step-by-step setup and performance validation.

minutes_to_complete: 120

who_is_this_for: This is an advanced topic for data engineers, platform engineers, and developers who want to build and optimize high-performance Spark SQL workloads using native execution engines on Arm-based cloud environments.

learning_objectives:
  - Install and configure Hadoop, Spark, and Hive on Azure Arm64 virtual machines (VMs).
  - Build and integrate Gluten with the Velox backend for native query execution.
  - Configure Spark SQL for columnar and vectorized execution.
  - Generate and load TPC-DS datasets for benchmarking.
  - Run Spark SQL workloads and compare performance between vanilla Spark and Gluten with Velox.

prerequisites:
  - A [Microsoft Azure account](https://azure.microsoft.com/) with access to Cobalt 100-based instances (Dpsv6)
  - Basic understanding of distributed systems and Apache Spark

# START generated_summary_faq
generated_summary_faq:
  template_version: summary-faq-v3
  generated_at: '2026-11-25T17:32:47Z'
  generator: ai
  ai_assisted: true
  ai_review_required: true
  model: gpt-5
  prompt_template: summary-faq-v3
  source_hash: a72f99d667f17bd8630d92af7223ab15895d8513779c1fe016ab5d104b6455dd
  summary_generated_at: '2026-11-25T17:32:47Z'
  summary_source_hash: a72f99d667f17bd8630d92af7223ab15895d8513779c1fe016ab5d104b6455dd
  faq_generated_at: '2026-11-25T17:32:47Z'
  faq_source_hash: a72f99d667f17bd8630d92af7223ab15895d8513779c1fe016ab5d104b6455dd
  summary: >-
    You'll compare Apache Spark SQL query times with and without Gluten and Velox on Azure. First, you'll create an Arm64 VM and install Hadoop, Spark, Hive, and the Gluten backend.
    You'll then generate TPC-DS data, convert it to Parquet, and run five analytical queries in
    local mode. Finally, you'll enable Gluten with Velox and compare the recorded times of the same queries.
  faqs:
  - question: What roles do Gluten and Velox play in the Spark setup?
    answer: >-
      You use Gluten as a Spark plugin that routes supported SQL operations to a backend.
      Velox is the vectorized C++ engine that processes those operations in columnar format.
  - question: How do I prepare the Hive metastore for Spark SQL?
    answer: >-
      Create a MySQL database for the metastore. Configure Hive to connect to it
      through the MySQL JDBC connector, and initialize the schema. This lets Spark use
      Hive tables for SQL analytics.
  - question: Why do I need to configure a hostname?
    answer: >-
      Set the hostname to `spark-master` and add it to `/etc/hosts` so that Hadoop and Spark
      can resolve the local node during service startup.
  - question: Why does the benchmark run Spark in local mode and use Parquet?
    answer: >-
      You run the five SQL queries in local mode on Parquet data to reduce schema mismatches
      and resource contention.
  - question: How do I compare vanilla Spark with Gluten and Velox, and what should I record?
    answer: >-
      Run the same five TPC-DS queries with default Spark and then with Gluten and Velox
      enabled. Compare the time it takes for each query to run.
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
  - Hadoop
  - Hive
  - Gluten
  - Velox

operatingsystems:
    - Linux

further_reading:
  - resource:
      title: Apache Spark Documentation
      link: https://spark.apache.org/docs/latest/
      type: documentation
  - resource:
      title: Gluten Project (Apache Incubator)
      link: https://github.com/apache/incubator-gluten
      type: documentation
  - resource:
      title: Velox Execution Engine
      link: https://github.com/facebookincubator/velox
      type: documentation
  - resource:
      title: TPC-DS Benchmark Overview
      link: https://www.tpc.org/tpcds/
      type: documentation

### FIXED, DO NOT MODIFY
# ================================================================================
weight: 1
layout: "learningpathall"
learning_path_main_page: "yes"
---
