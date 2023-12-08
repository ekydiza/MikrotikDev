---
weight: 350
title: "Preventing ICMP Smurf Attack"
description: ""
icon: "lock"
date: "2023-08-26T20:43:23+01:00"
lastmod: "2023-08-26T20:43:23+01:00"
aliases:
    - ../guides/security
draft: false
toc: true

---

```
/ip firewall raw
add action=drop chain=prerouting comment="Preventing ICMP Smurf Attack" dst-address-type=broadcast protocol=icmp
/ip firewall filter
add action=drop chain=input comment="Block Ping (ICMP) From WAN" in-interface=pppoe-out1 protocol=icmp
```