---
title: "TrueNAS basic settings!"
date: 2022-01-01T15:34:30-04:00
categories:
  - blog
tags:
  - Jekyll
  - update
---
  These are the basic settings I use on a fresh install of FreeNAS. This is for my personal use so some things may not apply to your situation. I made it public becuse it may help others.
```
ACCOUNTS
Add email address to root user
SYSTEM
general: select freenas cert and check WebGUI HTTP -> HTTPS Redirect
https port 443
Change Timezone
advance: enable show console message
email: setup gmail smtp using using 587 tls
alert services:add email address
SSH connections: generate key pairs, store keypairs in safe place, add public key to account user profile

TASKS
cron jobs: add report.sh script to cron job and set too "0 06 2,6,11,16,21,26 * *"
SMART tests: (long 1,15)(short 6,11,21,26)
snapshots task: not done yet
scrub tasks: set scrubs (2,17)

NETWORK 
global: not done yet - default ipv4 gateway 10.68.69.1, domain yourdomain.com, nameservers 1.1.1.1/8.8.4.4/10.68.69.1
interfaces:add igb0 interface and set DHCP, add igb1 interface and set DHCP

SHARING
unix shares: create an nfs share /mnt/myVol/appsNFS place a check for all dirs, Advance settings: mapall root:wheel
windows shares: create a smb share for media and shares, allow guest access, not done yet- tighten security

SERVICES
NFS service:select Allow non-root mount, Enable NFSv4, NFSv3 ownership model for NFSv4
Smart:add email for alerts, set critical 41 & difference 5
ups:select driver,shutdown timer "350", shut down command "shutdown -p now", warn time 60,add password, add email address and enable
enable smb, nfs, ssh, ups sevice to auto start



OTHER STUFF
edited jacket jail config.json for vnet interface "auto" fixed default interface not being added to bridge0
not done:
fix attach boot mirror check forum post and make issue
```

