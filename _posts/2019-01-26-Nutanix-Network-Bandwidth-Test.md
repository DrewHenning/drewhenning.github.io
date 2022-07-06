---
title: Nutanix Network Bandwidth Test
date: 2019-01-26 17:00:00 -0600
categories: [Nutanix]
tags: [ahv,cvm,iperf,networking]     # TAG names should always be lowercase
---

Here’s a quick script to check the network bandwidth/throughput on a Nutanix cluster. SSH into a Nutanix CVM and run:

```bash
allssh ./diagnostics/diagnostics.py run_iperf
```

This will loop through each CVM and test network performance to the other CVM’s in the cluster. It leverages the `diagnostics.py` script that is builtin to each CVM.

**Use caution when executing this script** as [iPerf](https://iperf.fr/) is designed to push the network bandwidth to the max. I typically only use this when setting up a new cluster to validate network performance or if troubleshooting a network performance issue.

In the example below, you can see we are getting close to line-rate speeds between CVM’s on a 10Gbps network.

```bash
login as: nutanix
Nutanix Controller VM
nutanix@NTNX-CLUSTER password:
Last login: Wed Nov 11 09:41:00 2018 from 10.20.30.108
nutanix@NTNX-8675309-A-CVM:10.20.30.103:~$ allssh ./diagnostics/diagnostics.py run_iperf
================== 10.20.30.101 =================
Running Iperf Test between CVMs
bandwidth between 10.20.30.101 and 10.20.30.102 is: 9.44 Gbits
bandwidth between 10.20.30.101 and 10.20.30.103 is: 9.41 Gbits
bandwidth between 10.20.30.101 and 10.20.30.104 is: 9.49 Gbits
bandwidth between 10.20.30.101 and 10.20.30.105 is: 9.34 Gbits
bandwidth between 10.20.30.101 and 10.20.30.106 is: 9.44 Gbits
bandwidth between 10.20.30.101 and 10.20.30.107 is: 9.46 Gbits
bandwidth between 10.20.30.101 and 10.20.30.108 is: 9.45 Gbits
================== 10.20.30.102 =================
Running Iperf Test between CVMs
bandwidth between 10.20.30.102 and 10.20.30.101 is: 9.45 Gbits
bandwidth between 10.20.30.102 and 10.20.30.103 is: 9.47 Gbits
bandwidth between 10.20.30.102 and 10.20.30.104 is: 9.47 Gbits
bandwidth between 10.20.30.102 and 10.20.30.105 is: 9.45 Gbits
bandwidth between 10.20.30.102 and 10.20.30.106 is: 9.42 Gbits
bandwidth between 10.20.30.102 and 10.20.30.107 is: 9.46 Gbits
bandwidth between 10.20.30.102 and 10.20.30.108 is: 9.4 Gbits
================== 10.20.30.103 =================
Running Iperf Test between CVMs
bandwidth between 10.20.30.103 and 10.20.30.101 is: 9.43 Gbits
bandwidth between 10.20.30.103 and 10.20.30.102 is: 9.45 Gbits
bandwidth between 10.20.30.103 and 10.20.30.104 is: 9.4 Gbits
bandwidth between 10.20.30.103 and 10.20.30.105 is: 9.44 Gbits
bandwidth between 10.20.30.103 and 10.20.30.106 is: 9.42 Gbits
bandwidth between 10.20.30.103 and 10.20.30.107 is: 9.48 Gbits
bandwidth between 10.20.30.103 and 10.20.30.108 is: 9.43 Gbits
================== 10.20.30.104 =================
Running Iperf Test between CVMs
bandwidth between 10.20.30.104 and 10.20.30.101 is: 9.46 Gbits
bandwidth between 10.20.30.104 and 10.20.30.102 is: 9.49 Gbits
bandwidth between 10.20.30.104 and 10.20.30.103 is: 9.43 Gbits
bandwidth between 10.20.30.104 and 10.20.30.105 is: 9.46 Gbits
bandwidth between 10.20.30.104 and 10.20.30.106 is: 9.45 Gbits
bandwidth between 10.20.30.104 and 10.20.30.107 is: 9.43 Gbits
bandwidth between 10.20.30.104 and 10.20.30.108 is: 9.48 Gbits
================== 10.20.30.105 =================
Running Iperf Test between CVMs
bandwidth between 10.20.30.105 and 10.20.30.101 is: 9.47 Gbits
bandwidth between 10.20.30.105 and 10.20.30.102 is: 9.48 Gbits
bandwidth between 10.20.30.105 and 10.20.30.103 is: 9.43 Gbits
bandwidth between 10.20.30.105 and 10.20.30.104 is: 9.48 Gbits
bandwidth between 10.20.30.105 and 10.20.30.106 is: 9.46 Gbits
bandwidth between 10.20.30.105 and 10.20.30.107 is: 9.36 Gbits
bandwidth between 10.20.30.105 and 10.20.30.108 is: 9.46 Gbits
================== 10.20.30.106 =================
Running Iperf Test between CVMs
bandwidth between 10.20.30.106 and 10.20.30.101 is: 9.45 Gbits
bandwidth between 10.20.30.106 and 10.20.30.102 is: 9.44 Gbits
bandwidth between 10.20.30.106 and 10.20.30.103 is: 9.43 Gbits
bandwidth between 10.20.30.106 and 10.20.30.104 is: 9.48 Gbits
bandwidth between 10.20.30.106 and 10.20.30.105 is: 9.43 Gbits
bandwidth between 10.20.30.106 and 10.20.30.107 is: 9.44 Gbits
bandwidth between 10.20.30.106 and 10.20.30.108 is: 9.47 Gbits
================== 10.20.30.107 =================
Running Iperf Test between CVMs
bandwidth between 10.20.30.107 and 10.20.30.101 is: 9.43 Gbits
bandwidth between 10.20.30.107 and 10.20.30.102 is: 9.41 Gbits
bandwidth between 10.20.30.107 and 10.20.30.103 is: 9.45 Gbits
bandwidth between 10.20.30.107 and 10.20.30.104 is: 9.41 Gbits
bandwidth between 10.20.30.107 and 10.20.30.105 is: 9.48 Gbits
bandwidth between 10.20.30.107 and 10.20.30.106 is: 9.46 Gbits
bandwidth between 10.20.30.107 and 10.20.30.108 is: 9.42 Gbits
================== 10.20.30.108 =================
Running Iperf Test between CVMs
bandwidth between 10.20.30.108 and 10.20.30.101 is: 9.44 Gbits
bandwidth between 10.20.30.108 and 10.20.30.102 is: 9.46 Gbits
bandwidth between 10.20.30.108 and 10.20.30.103 is: 9.43 Gbits
bandwidth between 10.20.30.108 and 10.20.30.104 is: 9.4 Gbits
bandwidth between 10.20.30.108 and 10.20.30.105 is: 9.44 Gbits
bandwidth between 10.20.30.108 and 10.20.30.106 is: 9.47 Gbits
bandwidth between 10.20.30.108 and 10.20.30.107 is: 9.43 Gbits
nutanix@NTNX-8675309-A-CVM:10.20.30.103:~$
```