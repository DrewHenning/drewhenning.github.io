---
title: Test Network Ports on Nutanix CVMs
date: 2018-12-12 17:00:00 -0600
categories: [Nutanix]
tags: [ahv,cvm,networking]     # TAG names should always be lowercase
---

Every now and then you’ll need to test connectivity on Nutanix CVM’s. For example, if you are setting up replication on Nutanix you’ll need TCP port 2020 open between the clusters.

In Windows I would test this using telnet but since the Nutanix CVM’s are based on linux we need to use the netcat (nc) command.

For example, if I wanted to test TCP port 2020 between clusters, I would SSH into a CVM and run:

```bash
nc -v -w 2 10.20.30.40 -z 2020
```

Where 10.20.30.40 is the remote IP I want to test connectivity to.

Below is an example of testing TCP 2009 and 2020 to a remote cluster. You can see that port 2009 is not open as the connection times out, while 2020 is open.

![Console Output](/assets/img/2018-12-12-nc-output.jpg)