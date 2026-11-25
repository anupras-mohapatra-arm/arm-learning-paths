---
title: Run Text Classification with ThirdAI on Arm servers

minutes_to_complete: 10

who_is_this_for: This is for software developers who want to learn how to run text classification tasks with ThirdAI on Arm servers.

learning_objectives: 
    - Train, evaluate, and deploy a ThirdAI model.
    - Set up an Arm server for text classification tasks with ThirdAI.

prerequisites:
    - An [Arm-based instance](/learning-paths/servers-and-cloud-computing/csp/) from a cloud service provider, or an on-premise Arm server

# START generated_summary_faq
generated_summary_faq:
  template_version: summary-faq-v3
  generated_at: '2026-11-25T17:37:18Z'
  generator: ai
  ai_assisted: true
  ai_review_required: true
  model: gpt-5
  prompt_template: summary-faq-v3
  source_hash: f6d8ac24a815f3c569f4fd50e747377ff47ed3560d927048c00b2fd1028a94e3
  summary_generated_at: '2026-11-25T17:37:18Z'
  summary_source_hash: f6d8ac24a815f3c569f4fd50e747377ff47ed3560d927048c00b2fd1028a94e3
  faq_generated_at: '2026-11-25T17:37:18Z'
  faq_source_hash: f6d8ac24a815f3c569f4fd50e747377ff47ed3560d927048c00b2fd1028a94e3
  summary: >-
    You'll train and evaluate a ThirdAI sentiment classifier on an Arm-based Linux server. First, you'll
    create a Python virtual environment, install the dependencies, and download the Amazon Polarity
    dataset. You'll then train a text classifier and save its model. Finally, you'll load the model and
    evaluate it on the test data. You'll classify two example product reviews as positive or negative.
  faqs:
  - question: How do I know that the Python virtual environment is active before installing packages?
    answer: >-
      Look for `(thirdai)` at the start of your shell prompt. If it's absent, run
      `source thirdai/bin/activate`.
  - question: Do I need to call `thirdai.licensing.activate()` before loading or evaluating the
      model?
    answer: >-
      Yes. Keep the `thirdai.licensing.activate(...)` call shown in `evaluate.py` before you
      load the saved model.
  - question: Which fields from the Amazon Polarity dataset does the model use?
    answer: >-
      The `title` field is the text input and its `label` is the target
      category. The training script saves these fields from the train and test splits
      in separate tab-separated files.
  - question: Which test data file does `evaluate.py` expect?
    answer: >-
      Use `amazon_polarity_test.csv`. Check that
      `test_filename` points to the file when you run `evaluate.py`.
  - question: What result should I expect when I run the evaluation and a quick prediction?
    answer: >-
      You should see a `categorical_accuracy` metric for the test data, followed by class labels
      `1` and `0` for the positive and negative sample reviews. The script prints these labels
      after converting the `model.predict` outputs to predicted classes.
# END generated_summary_faq

author: David Torres

generate_summary_faq: false
rerun_summary: false
rerun_faqs: false

### Tags
skilllevels: Introductory
subjects: AI/ML
platforms:
  - AWS Graviton
  - Microsoft Azure Cobalt
  - Google Axion
  - Oracle Cloud Infrastructure (OCI) Ampere Compute
armips:
    - Neoverse
tools_software_languages:
    - Python
    - ThirdAI
operatingsystems:
    - Linux

further_reading:
    - resource:
        title: ThirdAI Demos Repository
        link: https://github.com/ThirdAILabs/Demos
        type: documentation
    - resource:
        title: ThirdAI Website
        link: https://www.thirdai.com
        type: blog

### FIXED, DO NOT MODIFY
# ================================================================================
weight: 1                       # _index.md always has weight of 1 to order correctly
layout: "learningpathall"       # All files under learning paths have this same wrapper
learning_path_main_page: "yes"  # This should be surfaced when looking for related content. Only set for _index.md of learning path content.
---

