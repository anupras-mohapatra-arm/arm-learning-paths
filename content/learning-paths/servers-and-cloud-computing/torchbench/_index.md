---
title: Measure and accelerate PyTorch Inference on Arm servers

minutes_to_complete: 20

who_is_this_for: This is an introductory topic for software developers who want to learn how to measure and accelerate the performance of Natural Language Processing (NLP), vision and recommender PyTorch models on Arm-based servers.

learning_objectives:
    - Download and install the PyTorch Benchmarks suite.
    - Evaluate PyTorch model inference performance on an Arm-based server using the PyTorch Benchmark suite.
    - Compare the model inference performance using eager mode and `torch.compile` mode in PyTorch.

prerequisites:
    - An [Arm-based instance](/learning-paths/servers-and-cloud-computing/csp/) from a cloud service provider, or an on-premise Arm server

# START generated_summary_faq
generated_summary_faq:
  template_version: summary-faq-v3
  generated_at: '2026-11-25T17:39:31Z'
  generator: ai
  ai_assisted: true
  ai_review_required: true
  model: gpt-5
  prompt_template: summary-faq-v3
  source_hash: 6ad3f11220030e45ed3f671bc724e66ab10705c85634de13471bb2de365901a2
  summary_generated_at: '2026-11-25T17:39:31Z'
  summary_source_hash: 6ad3f11220030e45ed3f671bc724e66ab10705c85634de13471bb2de365901a2
  faq_generated_at: '2026-11-25T17:39:31Z'
  faq_source_hash: 6ad3f11220030e45ed3f671bc724e66ab10705c85634de13471bb2de365901a2
  summary: >-
    You'll benchmark PyTorch inference latency on an Arm-based Ubuntu server and compare eager mode
    with `torch.compile`. First, you'll install PyTorch and clone the PyTorch Benchmarks repository
    at the specified commit. You'll then install the listed NLP, vision, and recommender models and
    configure the example environment. Finally, you'll run the same model list in both modes and
    compare the latency values saved in the benchmark results.
  faqs:
  - question: What should I do if model installation fails with Python 3.12?
    answer: >-
      If `install.py` reports that `pkgutil` has no `ImpImporter` attribute, change the
      pinned NumPy version in `requirements.txt` to `numpy~=1.26.4`.
  - question: How do I know that the PyTorch Benchmarks suite installed correctly?
    answer: >-
      Run `python3 run_benchmark.py cpu` for the installed model list.
      You should get a timestamped results directory with inference latency metrics.
  - question: What should I configure before comparing the two benchmark modes?
    answer: >-
      Set the environment variables for BF16 math, Transparent Huge Page
      allocations, cache capacity, and the number of threads. Keep these settings consistent
      when you run the eager and `torch.compile` benchmarks.
  - question: How do I compare eager mode with torch.compile?
    answer: >-
      Run the documented `run_benchmark.py` command without `--torchdynamo` for eager mode,
      then use `--torchdynamo inductor` for `torch.compile`. You can compare the latency of each model
      in the saved results.
  - question: What result should I expect after a successful benchmark run?
    answer: >-
      Look in `.userbenchmark/cpu/` for the timestamped `metrics-YYmmddHHMMSS.json` file.
      You should find inference latency values in milliseconds for the models that you ran.
# END generated_summary_faq

author: Pareena Verma

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
operatingsystems:
    - Linux
tools_software_languages:
    - Python
    - PyTorch

further_reading:
    - resource:
        title: PyTorch Benchmarks
        link: https://github.com/pytorch/benchmark
        type: website
    - resource:
        title: PyTorch Inference Performance Tuning on AWS Graviton Processors
        link: https://pytorch.org/tutorials/recipes/inference_tuning_on_aws_graviton.html
        type: documentation
    - resource:
        title: ML inference on Graviton CPUs with PyTorch
        link: https://github.com/aws/aws-graviton-getting-started/blob/main/machinelearning/pytorch.md
        type: documentation
    - resource:
        title: PyTorch Documentation
        link: https://pytorch.org/docs/stable/index.html
        type: documentation

### FIXED, DO NOT MODIFY
# ================================================================================
weight: 1                       # _index.md always has weight of 1 to order correctly
layout: "learningpathall"       # All files under learning paths have this same wrapper
learning_path_main_page: "yes"  # This should be surfaced when looking for related content. Only set for _index.md of learning path content.
---

