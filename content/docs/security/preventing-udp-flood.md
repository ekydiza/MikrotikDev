---
weight: 350
title: "Preventing UDP Flood Attack"
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
UDP flood on MikroTik refers to a type of cyber attack where the User Datagram Protocol (UDP) is exploited to overwhelm and flood a MikroTik device with a large volume of UDP packets. UDP flood attacks aim to saturate the target's network bandwidth, causing congestion and disrupting normal operations. Unlike TCP, UDP is connectionless and does not establish a session before transmitting data, making it susceptible to abuse. Attackers often use various techniques to generate and send a massive number of UDP packets to the target, leading to network degradation or even service unavailability. 


## Steps

```
/ip firewall raw
add action=drop chain=prerouting comment="Preventing UDP Flood Attack" dst-port=53 in-interface=pppoe-out1 protocol=udp
add action=accept chain=prerouting dst-port=53 in-interface=!pppoe-out1 limit=100,5:packet protocol=udp
add action=drop chain=prerouting dst-port=53 in-interface=!pppoe-out1 protocol=udp
```

after that,
> IP > DNS and disable “Allow Remote Requests”
