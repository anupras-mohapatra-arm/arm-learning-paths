---
title: Deploy a TimescaleDB and Grafana live sensor dashboard on Google Axion

minutes_to_complete: 45

who_is_this_for: This is an introductory topic for DevOps engineers, database engineers, and software developers who want to deploy and operate TimescaleDB on SUSE Linux Enterprise Server (SLES) Arm64, ingest live time-series sensor data, and visualize it in Grafana.

learning_objectives:
  - Install and configure TimescaleDB on Google Cloud C4A virtual machines (VMs) by building from source for Arm64.
  - Create a real-time sensor data ingestion pipeline using Python with hypertables, continuous aggregates, and retention policies.
  - Build a live sensor dashboard with Grafana that automatically refreshes to display time-series data.
  - Validate end-to-end data flow from ingestion through TimescaleDB to Grafana visualization.

prerequisites:
  - A [Google Cloud Platform (GCP)](https://cloud.google.com/free) account with billing enabled
  - Basic familiarity with SQL, Python, and Grafana

# START generated_summary_faq
generated_summary_faq:
  template_version: summary-faq-v3
  generated_at: '2026-11-25T17:38:00Z'
  generator: ai
  ai_assisted: true
  ai_review_required: true
  model: gpt-5
  prompt_template: summary-faq-v3
  source_hash: b0ed0f2784830d54777d7451517b4cb5c1a37b4e084f5b6f8bc8063793d50b1a
  summary_generated_at: '2026-11-25T17:38:00Z'
  summary_source_hash: b0ed0f2784830d54777d7451517b4cb5c1a37b4e084f5b6f8bc8063793d50b1a
  faq_generated_at: '2026-11-25T17:38:00Z'
  faq_source_hash: b0ed0f2784830d54777d7451517b4cb5c1a37b4e084f5b6f8bc8063793d50b1a
  summary: >-
    You'll deploy a TimescaleDB and Grafana sensor dashboard on a Google Cloud C4A VM.
    First, you'll create the VM and open the Grafana network port. You'll then build TimescaleDB on SUSE
    Linux Enterprise Server, write simulated sensor readings to a hypertable, and configure
    retention and continuous aggregates. Finally, you'll connect Grafana to TimescaleDB and build
    a dashboard that displays the incoming temperature readings.
  faqs:
  - question: Which Google Cloud machine type should I pickce?
    answer: >-
      Choose `c4a-standard-4`, which provides four vCPUs and 16 GB of memory.
      The VM hosts TimescaleDB and Grafana.
  - question: Which port do I need to open in the firewall, and how do I confirm access?
    answer: >-
      Open TCP port `3000` for Grafana. You can check access by opening
      `http://<VM-PUBLIC-IP>:3000` in your browser after Grafana starts.
  - question: Which PostgreSQL and TimescaleDB versions do I build?
    answer: >-
      Use PostgreSQL 15 and build the TimescaleDB 2.25.0 extension from source on the VM.
  - question: Which Python package do I use to write sensor readings to TimescaleDB?
    answer: >-
      Install `python3-psycopg2` and use `psycopg2` in your Python sensor script to insert
      readings into the `sensor_data` hypertable.
  - question: How do I verify the sensor-to-dashboard pipeline?
    answer: >-
      Check that the row count in `sensor_data` increases, then watch the Grafana dashboard
      refresh with new temperature readings.
# END generated_summary_faq

author: Pareena Verma

generate_summary_faq: false
rerun_summary: false
rerun_faqs: false

##### Tags
skilllevels: Introductory
subjects: Databases
platforms:
  - Google Axion

armips:
  - Neoverse

tools_software_languages:
  - TimescaleDB
  - PostgreSQL
  - Python
  - Grafana
  - psycopg2

operatingsystems:
  - Linux

# ================================================================================
#       FIXED, DO NOT MODIFY
# ================================================================================

further_reading:
  - resource:
      title: TimescaleDB official documentation
      link: https://docs.timescale.com/
      type: documentation

  - resource:
      title: PostgreSQL 15 documentation
      link: https://www.postgresql.org/docs/15/index.html
      type: documentation

  - resource:
      title: Grafana documentation
      link: https://grafana.com/docs/grafana/latest/
      type: documentation

  - resource:
      title: Python psycopg2 documentation
      link: https://www.psycopg.org/docs/
      type: documentation

weight: 1
layout: "learningpathall"
learning_path_main_page: yes
---

