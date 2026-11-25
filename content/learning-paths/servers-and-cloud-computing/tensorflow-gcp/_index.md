---
title: Deploy TensorFlow on Google Cloud C4A virtual machines
minutes_to_complete: 30

who_is_this_for: This is an introductory topic for software developers deploying and optimizing TensorFlow workloads on Arm64 Linux environments, specifically using Google Cloud C4A virtual machines (VMs) powered by Axion processors.

learning_objectives:
  - Provision an Arm-based SUSE Linux Enterprise Server (SLES) VM on Google Cloud.
  - Install TensorFlow on a SUSE Arm64 C4A instance.
  - Verify TensorFlow by running computation and model training tests on Arm64.
  - Benchmark TensorFlow using TensorFlow Keras (`tf.keras`) to evaluate inference speed and model performance on Arm64 systems.

prerequisites:
  - A [Google Cloud Platform (GCP)](https://cloud.google.com/free) account with billing enabled
  - Basic familiarity with [TensorFlow](https://www.tensorflow.org/)

# START generated_summary_faq
generated_summary_faq:
  template_version: summary-faq-v3
  generated_at: '2026-11-25T17:36:36Z'
  generator: ai
  ai_assisted: true
  ai_review_required: true
  model: gpt-5
  prompt_template: summary-faq-v3
  source_hash: 6d71ea453d51ba0bcd09014f60f79f0fadf472ae4a1393b745e61920120d3365
  summary_generated_at: '2026-11-25T17:36:36Z'
  summary_source_hash: 6d71ea453d51ba0bcd09014f60f79f0fadf472ae4a1393b745e61920120d3365
  faq_generated_at: '2026-11-25T17:36:36Z'
  faq_source_hash: 6d71ea453d51ba0bcd09014f60f79f0fadf472ae4a1393b745e61920120d3365
  summary: >-
    You'll deploy TensorFlow on a Google Cloud C4A VM and benchmark model inference on
    its Arm CPU. First, you'll create a SUSE Linux Enterprise Server VM and install TensorFlow in a
    Python environment. You'll then confirm that TensorFlow detects the CPU and run computation and
    neural network checks. Finally, you'll benchmark ResNet50, MobileNetV2, and InceptionV3 with
    random input and inspect inference time and throughput.
  faqs:
  - question: Which virtual machine configuration should I choose?
    answer: >-
      Choose the C4A series, the `c4a-standard-4` machine type, and a SUSE Linux Enterprise Server
      (SLES) Arm64 image.
  - question: What baseline tests do I perform before benchmarking?
    answer: >-
      Multiply two matrices to check TensorFlow computation on the CPU. Then, train a
      small neural network on random data to check that model training runs.
  - question: What output should I expect from tf.config.list_physical_devices()?
    answer: >-
      You should see a CPU device similar to
      `PhysicalDevice(name='/physical_device:CPU:0', device_type='CPU')` in the returned list.
  - question: Do I need a GPU to run the tests and benchmarks?
    answer: >-
      No. The baseline tests and benchmarks run on the CPU.
  - question: How do I confirm that benchmarking worked?
    answer: >-
      Look for the average inference time and throughput for ResNet50, MobileNetV2,
      and InceptionV3. You should see a result for each model in the console.
# END generated_summary_faq

author: Pareena Verma

generate_summary_faq: false
rerun_summary: false
rerun_faqs: false

##### Tags
skilllevels: Introductory
subjects: AI/ML
platforms:
  - Google Axion

armips:
  - Neoverse

tools_software_languages:
  - TensorFlow
  - Python
  - Keras

operatingsystems:
  - Linux

# ================================================================================
#       FIXED, DO NOT MODIFY
# ================================================================================
further_reading:
  - resource:
      title: Google Cloud documentation
      link: https://cloud.google.com/docs
      type: documentation
  - resource:
      title: TensorFlow documentation
      link: https://www.tensorflow.org/learn
      type: documentation
  - resource:
      title: Phoronix Test Suite (PTS) documentation
      link: https://www.phoronix-test-suite.com/
      type: documentation

weight: 1
layout: "learningpathall"
learning_path_main_page: "yes"
---

