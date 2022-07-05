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
All good
