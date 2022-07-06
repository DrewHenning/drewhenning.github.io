---
title: Nutanix AHV - Network LLDP/CDP Information
date: 2020-12-03 17:00:00 -0600
categories: [Nutanix]
tags: [ahv,networking]     # TAG names should always be lowercase
---

Nutanix AHV is able to receive Link Layer Discovery Protocol (LLDP) and Cisco Discovery Protocol (CDP) from the upstream switches they are connected to.

To receive LLDP/CDP information can run lldpctl from an AHV host. If you’d like to pull the information from all nodes in a cluster, SSH into a Nutanix CVM and run:

```bash
hostssh lldpctl
```
![Command Output](/assets/img/2020-12-03-image01.png)

This is a great way to see details on what switch ports your Nutanix nodes are connected to.

You can also get the switch port details on the Network page from Nutanix Prism. It can give a nice visual of the physical network connections.

![Prism Network View](/assets/img/2020-12-03-image02.png)

By default the Nutanix AHV hypervisor is set to receive-only for LLDP/CDP info from the network.  You can enable the virtual switch in AHV to transmit (TX) LLDP/CDP info. This allows the network administrator to see the AHV hosts on the network by running show lldp neighbor or show cdp neighbor or similar on the upstream swtich.

This setting is configured from the command line on a Nutanix CVM. To get the current setting run:

```bash
ncli cluster get-hypervisor-lldp-config
```

To enable LLDP transmit on a cluster run:

```bash
ncli cluster edit-hypervisor-lldp-params enable-lldp-tx=true
```

I’m a big fan of leveraging LLDP/CDP info instead of going into datacenters and manually tracing cables. Hopefully this can help you when troubleshooting or validating physical network connectivity.