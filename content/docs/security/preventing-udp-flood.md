---
weight: 350
title: "Preventing Brute Force Attack"
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
add action=drop chain=prerouting comment="Preventing UDP Flood Attack" dst-port=53 in-interface=pppoe-out1 protocol=udp
add action=accept chain=prerouting dst-port=53 in-interface=!pppoe-out1 limit=100,5:packet protocol=udp
add action=drop chain=prerouting dst-port=53 in-interface=!pppoe-out1 protocol=udp
```

**Step:** IP > DNS dan disable *"Allow Remote Requests"*
