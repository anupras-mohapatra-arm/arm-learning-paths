---
title: Connect to the Zena CSS Linux guest
weight: 5

### FIXED, DO NOT MODIFY
layout: learningpathall
---

## Check the mapping and guest listener

After observing the Zena CSS boot, you can connect to the Linux guest using Architecture Native Acceleration (ANA) port mapping. 

Find the port mapping of the virtual platform and authorize an SSH tunnel. Connect through the external port mapped to guest port `22`. The port and target address belong to the selected virtual platform. Get the port and target address from ANA each time rather than copying values from another project.

In **Lab Manager > Networking > Port Mapping** (or **Device Access Ports**), select the Zena virtual platform that you started.

![ANA Port Mapping panel with the Authorize button and generated SSH tunnel command#center](ana_port_mapping.png "Authorize an ANA SSH tunnel")

Find the TCP entry whose **target port** is `22`. Record its target IP and external port in your private run notes. Read the network prefix from the guest interface. Don't treat every listed external port as an SSH port.

![ANA Port Mapping table showing the external TCP port mapped to guest port 22#center](ana_port_mapping2.png "Find the SSH port mapping")

On the **primary-compute Linux console**, inspect the guest network and SSH service:

```bash
ip -4 -br addr
systemctl is-active sshd.socket
```

The tested guest returned:

```output
lo               UNKNOWN        127.0.0.1/8
eth0             UP             192.168.122.153/24 metric 10
active
```

Compare the target IP in the ANA port mapping with the addresses shown by `ip -br addr`. If they differ, confirm that the mapping belongs to the virtual platform. For the example Zena run, the mapping targeted `192.168.122.39`, while `eth0` had `192.168.122.153/24` from DHCP. Both addresses are in the same `/24` subnet. 

Add the mapped target IP temporarily as a second address on `eth0`, replacing `192.168.122.39` with your target IP:

```bash
ip addr add 192.168.122.39/24 dev eth0
ip -4 addr show dev eth0 | grep 'inet '
```

The example output showed both `192.168.122.153/24` and `192.168.122.39/24`, with the latter marked `secondary`.

```
inet 192.168.122.153/24 metric 10 brd 192.168.122.255 scope global dynamic eth0
inet 192.168.122.39/24 scope global secondary eth0
```

Your output might differ. 

Use the target IP from your current mapping and the prefix for your guest subnet. Don't copy `192.168.122.39/24` unless it matches your virtual platform. This address is lost when the guest restarts.

The guest that was used to test the Learning Path reported `sshd.socket` as active. This doesn't confirm that the ANA tunnel works. If the socket is inactive on your image, start it and confirm it is active:

```bash
systemctl start sshd.socket
systemctl is-active sshd.socket
```


## Authorize the tunnel and connect

In ANA, select or register your local SSH public key and choose **Authorize** for the virtual platform. Copy the complete tunnel command that ANA generates and run it on your local computer. Keep that terminal open. 

In a second local terminal, enter the external port from the mapping whose target port is `22`:

```bash
printf 'External port mapped to guest port 22: '
read -r ANA_SSH_PORT
ssh -4 -p "$ANA_SSH_PORT" root@127.0.0.1
```

Run this command in the resulting guest SSH shell:

```bash
uname -m; hostname
```

The SSH shell returns `aarch64` for `uname -m` and `ana-rd-zena` for `hostname`. 

If the connection fails before SSH authentication, check the terminal running the ANA tunnel. In the example run, it initially reported `channel ... open failed: connect failed: No route to host`. The SSH connection succeeded after the mapped guest IP was added, without restarting the tunnel. 

If the error persists after confirming the guest address and SSH listener, give the chamber administrator the following details:

- Virtual platform name
- Current mapping
- Redacted tunnel error 

The chamber administrator can use this infomration to check the relay route.

## What you've accomplished and what's next

You've now reached the selected virtual platform from your development computer using its current ANA port mapping. Keep the authorized tunnel open.

Next, you'll exchange a file with the Linux guest.
