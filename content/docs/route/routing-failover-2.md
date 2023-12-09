---
weight: 350
title: "Port Knocking"
description: ""
icon: "lock"
date: "2023-08-26T20:43:23+01:00"
lastmod: "2023-08-26T20:43:23+01:00"
aliases:
    - ../guides/security
draft: false
toc: true

---

## Overview
Failover is ...

## Steps
example:
- WAN-1 = IP 192.168.2.2/24
- WAN-2 = IP 192.168.3.2/24

```
/ip route
add check-gateway=ping distance=1 gateway=192.168.2.1 target-scope=10
add check-gateway=ping distance=2 gateway=192.168.3.1 target-scope=10
```