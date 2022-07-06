---
title: Determine if Hyper-Threading is Enabled on a Nutanix AHV Host
date: 2020-10-01 17:00:00 -0600
categories: [Nutanix]
tags: [ahv]     # TAG names should always be lowercase
---

I had a customer ask if Hyper-Threading (HT) was enabled on their Nutanix AHV host. As of AOS 5.18 (Oct 2020) the HT status is not visible in Prism. You only see the actual cores on the host.

![Prism Output](/assets/img/2020-10-01_14-50-32-3.jpg)

To get the HT status, you have to jump into the CLI. SSH into a Nutanix CVM and run:

```bash
hostssh "lscpu | egrep '^Thread|^Core|^Socket|^CPU\('"
```

The `hostssh` macro will run the following command on all hypervisor hosts in the Nutanix cluster. Very helpful!

If Thread(s) per core is set to 2, then HT is enabled.

![Command Output](/assets/img/2020-09-30_14-49-55.jpg)

