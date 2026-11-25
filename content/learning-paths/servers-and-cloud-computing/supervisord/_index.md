---
title: Access running containers using Supervisor, SSH, and Remote.It

minutes_to_complete: 60

who_is_this_for: This is an introductory topic for software developers who want to learn how to run multiple services in a container and access running containers using Supervisor, SSH, and Remote.It during the debug and test phases of a project.

learning_objectives:
    - Use Supervisor to run multiple services in a container.
    - Access a container running in AWS Fargate without changing the security group for debug and test.

prerequisites:
    - An Arm Linux computer running Docker
    - An AWS account
    - A Remote.It account

# START generated_summary_faq
generated_summary_faq:
  template_version: summary-faq-v3
  generated_at: '2026-11-25T17:34:01Z'
  generator: ai
  ai_assisted: true
  ai_review_required: true
  model: gpt-5
  prompt_template: summary-faq-v3
  source_hash: 8445e26946d3aa2b12752d60ffed0543f45f7064b1b953de44e3d034b5666571
  summary_generated_at: '2026-11-25T17:34:01Z'
  summary_source_hash: 8445e26946d3aa2b12752d60ffed0543f45f7064b1b953de44e3d034b5666571
  faq_generated_at: '2026-11-25T17:34:01Z'
  faq_source_hash: 8445e26946d3aa2b12752d60ffed0543f45f7064b1b953de44e3d034b5666571
  summary: >-
    You access a running container over SSH through Remote.It while Supervisor manages its
    services. First, you build and run an Apache example container. You then update its
    `Dockerfile`, add `supervisord.conf`, register the container with Remote.It, and connect
    through the dashboard endpoint. Finally, you deploy the container to AWS Fargate with
    Copilot, configure Arm64 and the registration code, and connect again.
  faqs:
  - question: How do I know the container includes Supervisor, SSH, and Remote.It after the rebuild?
    answer: >-
      Start the rebuilt container with your Remote.It registration code. You should see the
      Apache welcome page locally and the device in your Remote.It dashboard. Then use the
      dashboard's **CONNECT** option and endpoint to open an SSH session.
  - question: Which files do I change to enable multiple services with Supervisor?
    answer: >-
      Replace `Dockerfile` with the supplied example and create `supervisord.conf`. You use
      these files to install SSH and Remote.It and tell Supervisor which services to start.
  - question: Do I need to open port 22 or modify the AWS security group when using Fargate?
    answer: >-
      You don't need to open port 22 or change the security group for SSH. The guide connects
      through Remote.It without sharing the container's SSH port.
  - question: What should I check if I cannot connect over SSH through Remote.It?
    answer: >-
      Check that you supplied your Remote.It registration code and that the device appears in
      your dashboard. Select **CONNECT**, copy the **PUBLIC ENDPOINT** values, and use those
      values in the SSH command shown in the guide.
  - question: How do I know the Fargate task is ready to access?
    answer: >-
      Wait for `copilot svc deploy` to finish, then look for the new device in your Remote.It
      dashboard. You can use its endpoint to connect over SSH.
# END generated_summary_faq

author: Jason Andrews

generate_summary_faq: false
rerun_summary: false
rerun_faqs: false

### Tags
skilllevels: Introductory
subjects: Performance and Architecture
platforms:
  - AWS Graviton
armips:
    - Neoverse 
    - Cortex-A
operatingsystems:
    - Linux 
tools_software_languages:
    - Docker
    - Remote.It
    - Supervisor

further_reading:
    - resource:
        title: Run multiple processes in a container
        link: https://docs.docker.com/config/containers/multi-service_container/
        type: documentation
    - resource:
        title: Supervisor with Docker Lessons learned
        link: https://advancedweb.hu/supervisor-with-docker-lessons-learned/
        type: blog
    - resource:
        title: Multiple services in a Docker container with supervisord
        link: https://dev.to/pratapkute/multiple-services-in-a-docker-container-with-supervisord-2g13
        type: blog

### FIXED, DO NOT MODIFY
# ================================================================================
weight: 1                       # _index.md always has weight of 1 to order correctly
layout: "learningpathall"       # All files under learning paths have this same wrapper
learning_path_main_page: "yes"  # This should be surfaced when looking for related content. Only set for _index.md of learning path content.
---

