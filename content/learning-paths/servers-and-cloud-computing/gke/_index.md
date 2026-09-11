---
title: Create an Arm-based Kubernetes cluster on Google Cloud Platform 
description: Learn how to automate the deployment of an Arm-based Google Kubernetes Engine cluster using Terraform for container orchestration.

minutes_to_complete: 60   

who_is_this_for: This is an advanced topic for software developers who want to deploy an Arm-based Kubernetes cluster using Google Kubernetes Engine (GKE).

learning_objectives:
    - Automate the deployment of an Arm-based GKE cluster using Terraform.

prerequisites:
    - A Google Cloud account
    - A computer with Terraform, Google Cloud CLI (`gcloud`), and Kubernetes CLI (`kubectl`) installed

# START generated_summary_faq
generated_summary_faq:
  template_version: summary-faq-v3
  generated_at: '2026-09-10T22:07:59Z'
  generator: ai
  ai_assisted: true
  ai_review_required: true
  model: gpt-5
  prompt_template: summary-faq-v3
  source_hash: a95252725acf608ef32919061f816a4dbcad53a1ce3039857d33e6692795c895
  summary_generated_at: '2026-09-10T22:07:59Z'
  summary_source_hash: a95252725acf608ef32919061f816a4dbcad53a1ce3039857d33e6692795c895
  faq_generated_at: '2026-09-10T22:07:59Z'
  faq_source_hash: a95252725acf608ef32919061f816a4dbcad53a1ce3039857d33e6692795c895
  summary: >-
    You'll automate an Arm-based GKE cluster with Terraform. First, you'll define the cluster and node pools, initialize the configuration, and provision the resources in Google Cloud. After deployment, you'll connect with `kubectl` and confirm that the nodes are ready. You'll then verify that the selected Arm node type and project settings produced a working cluster.
  faqs:
  - question: How do I know that my Terraform configuration targets Arm-based nodes?
    answer: >-
      Check the node pool machine type in your Terraform files and choose an Arm-based option
      supported by GKE, such as C4A or Tau T2A. Confirm the selection before applying
      the configuration.
  - question: What result should I expect when the deployment finishes?
    answer: >-
      Terraform reports successful creation and outputs cluster details. You can use `kubectl` to
      reach the cluster and see nodes in the `Ready` state.
  - question: What should I check if the apply step fails with project or permission errors?
    answer: >-
      Verify that the Google Cloud project exists and is specified in your Terraform configuration.
      Ensure the Google Cloud CLI is installed and authenticated for that project.
  - question: How do I verify that kubectl is pointing to the new cluster?
    answer: >-
      Configure `kubectl` for the cluster created by Terraform, then list the cluster nodes to confirm
      connectivity. If listing nodes fails, recheck your current `kubectl` context.
  - question: Can I run Terraform from my local workstation?
    answer: >-
      Yes. You can use any computer that has Terraform, `kubectl`, and the Google Cloud CLI installed.
# END generated_summary_faq

author: Jason Andrews

generate_summary_faq: false
rerun_summary: false
rerun_faqs: false

##### Tags
skilllevels: Advanced
subjects: Containers and Virtualization
platforms:
  - Google Axion

armips:
    - Neoverse

tools_software_languages:
    - Terraform
    - Kubernetes

operatingsystems:
    - Linux

# ================================================================================
#       FIXED, DO NOT MODIFY
# ================================================================================
further_reading:
    - resource:
        title: Create Arm based clusters and node pools 
        link: https://cloud.google.com/kubernetes-engine/docs/how-to/create-arm-clusters-nodes
        type: documentation
    - resource:
        title: Configure cluster access to use kubectl
        link: https://cloud.google.com/kubernetes-engine/docs
        type: documentation
    - resource:
        title: GKE documentation
        link: https://cloud.google.com/kubernetes-engine/docs
        type: documentation

weight: 1                       # _index.md always has weight of 1 to order correctly
layout: "learningpathall"       # All files under learning paths have this same wrapper
learning_path_main_page: "yes"  # Indicates this should be surfaced when looking for related content. Only set for _index.md of learning path content.
---
