---
weight: 350
title: "Blocking Facebook using TLS host"
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
add action=drop chain=forward dst-address-list=Facebook src-address=192.168.50.0/24 comment="Blocking Facebook on RouterOS using TLS Host"

/ip firewall mangle
add action=add-dst-to-address-list address-list=Facebook address-list-timeout=4w2d chain=prerouting dst-port=443 protocol=tcp tls-host=*.facebook.com comment="Detecting IP Addresses Facebook"
```

After putting the script on RouterOS. Please do this before using it.
1. Clear Traffic Connections on RouterOS.
   - IP -> Firewall -> Connections
   - Delete All Connections (Shortcut key: CTRL + A And Click remove button)
2. Clear Cache on your web browser.