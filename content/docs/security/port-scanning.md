---
weight: 350
title: "Drop Port Scan Attacks"
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
/ip firewall filter
add action=add-src-to-address-list address-list="Port Scan" address-list-timeout=4w2d chain=forward comment="Preventing Port Scan" protocol=tcp psd=21,3s,3,1
add action=add-src-to-address-list address-list="Port Scan" address-list-timeout=4w2d chain=input protocol=tcp psd=21,3s,3,1
add action=drop chain=forward src-address-list="Port Scan"
add action=drop chain=input src-address-list="Port Scan"
```

