---
title: How to upgrade Splunk on CentOS7
date: 2020-10-11 17:00:00 -0600
categories: [Splunk]
tags: [centos]     # TAG names should always be lowercase
---

I needed to upgrade a small Splunk server from 7.1.2 to 7.3.2 on a CentOS7. Overall the process was fairly straightforward, below were my steps. When in doubt, follow the official documentation from Splunk.

## Download the new version of Splunk

Grab the .tgz file for Splunk Enterprise – https://www.splunk.com/en_us/download/splunk-enterprise.html#tabs/linux In this case the file name was: `splunk-7.3.2-c60db69f8e32-Linux-x86_64.tgz`

## Stop the Splunk Server

SSH into the splunk server and run:

```bash
/opt/splunk/bin/splunk stop
```

## Snapshot the Splunk server

If your splunk server is virtualized, it never hurts to grab a snapshot before you do the upgrade.

## Upgrade Splunk

Assuming Splunk is installed to /opt/splunk, run the following command to upgrade splunk:

```bash
tar xvzf splunk-7.3.2-c60db69f8e32-Linux-x86_64.tgz -C /opt
```
## Run splunk after the upgrade
This will start Splunk after the upgrade and accept the license:

```bash
/opt/splunk/bin/splunk start --accept-license
```
Also set Splunk to auto start if the server is rebooted:

```bash
/opt/splunk/bin/splunk enable boot-start
```

## Delete your snapshot

If the upgrade appears to have been successful, don’t forget to delete your snapshot.