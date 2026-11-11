---
title: Create and start a Zena CSS virtual platform
weight: 3

### FIXED, DO NOT MODIFY
layout: learningpathall
---
## Create a new virtual-platform project

Use the Architecture Native Acceleration (ANA) Web IDE to create a new virtual-platform project. You'll use the supplied Edge Workload Abstraction and Orchestration Layer (EWAOL) images. You therefore don't need to build software before the first boot.

To create the project:

1. Sign in to the ANA chamber that's provided by your administrator and open the **Web IDE**.
2. Start the **Create a New Virtual Platform Project** workflow described in your Innexis ANA User Guide.
3. Select **Arm-Zena-CSS** as the vSoC.
4. Select **Arm-Zena-CSS EWAOL Software Stack** as the software stack.
5. Give the project a recognizable name and finish the creation workflow. Record any configuration option that you change from its default.

![ANA project form with Arm-Zena-CSS and its EWAOL software stack selected#center](create_zena_project.png "Create a Zena CSS virtual platform project")

The new project appears in the Web IDE with a Zena CSS virtual platform and its selected EWAOL software. Verify both selections before starting. Creating a project doesn't, by itself, show that Linux can boot.

![Zena CSS project and virtual SoC configuration in the ANA Web IDE#center](project_conf.png "Zena CSS project configuration")

{{% notice Note %}}
If the project workflow offers a different Zena or EWAOL variant, record its full name. Check with the chamber administrator before continuing. The prebuilt software needs to match the chamber host and vSoC configuration.
{{% /notice %}}

## Configure Host Access before starting

Set up the folder for file-sharing while the virtual platform is stopped. ANA disables **Host Filesystem - Access Path** and **Browse** while a virtual platform is running.

1. In the Web IDE **Explorer**, create a folder in your new project for the shared files, such as **test_folder**. The **New Folder** control is in the **WORKSPACE** section of Explorer.
2. Open **Lab Manager**, select the new virtual platform, and expand **Software > Host Access**.
3. Next to **Host Filesystem - Access Path**, choose **Browse**. The directory selector shows the ANA project workspace. Select the shared folder in your project.
4. Set **Host Filesystem - Guest Mount ID** to **share** and choose **Save**.

Confirm that **Access Path** shows the selected project folder and **Guest Mount ID** is **share** before choosing **Start**. You'll use this folder and mount ID for file sharing.

![ANA Host Access settings with a project folder and guest mount ID share#center](ana_host_access.png "Configure Host Access before starting")

## Start the virtual platform

To start the virtual platform:

1. Open **Lab Manager** from the Web IDE.
2. Select the virtual platform that you created.
3. Choose **Start**.
4. Open the **Serial Console** view and select the primary-compute console.

![ANA Lab Manager showing a stopped virtual platform and its Start button#center](ana_lab_manager_start.png "Start the Zena CSS virtual platform")

Lab Manager shows that the selected virtual platform is starting or running. The primary-compute console begins displaying boot messages. Boot might take time. Wait for a Linux login prompt before treating it as complete.

![Primary Compute serial console at the EWAOL Linux login prompt#center](primary_compute_console.png "EWAOL Linux login prompt")


{{% notice Note %}}
If the virtual platform stops before reaching a login prompt, record its Lab Manager state and the last visible console messages. After recording those values, retry. Check the selected vSoC, software stack, and chamber compatibility.
{{% /notice %}}


## Record the starting configuration

Keep a short record of the following settings:

- ANA release
- Chamber host type
- Project name
- vSoC selection
- Software-stack name

Also note any memory setting that you changed.

## What you've accomplished and what's next

You've started a new Zena CSS virtual platform in Innexis ANA. You're ready to continue when you can open the console for the same project that you started.

Next, you'll follow the boot sequence across the ANA consoles and inspect the Linux guest.
