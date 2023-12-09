---
weight: 350
title: "Data Limit on Trial Hotspot User"
description: ""
date: "2023-08-26T20:43:23+01:00"
lastmod: "2023-08-26T20:43:23+01:00"
aliases:
    - ../guides/hotspot
draft: false
toc: true

---

```
#Download limit in MB
:local downquotamb "50"

# Do not modify anything below
:local downquota [$downquotamb * 1000]
:local counter
:local datadown
:local username
:local macaddress
:foreach counter in=[/ip hotspot active find ] do={
:set datadown [/ip hotspot active get $counter bytes-out]
:if ($datadown>$downquota) do={
:set username [/ip hotspot active get $counter user]
:set macaddress [/ip hotspot active get $counter mac-address]
/ip hotspot user remove [/ip hotspot user find where name=$username]
/ip hotspot user add name=$username limit-bytes-out=$downquota mac-address=$macaddress
/ip hotspot active remove $counter
:log info "Logged out $username - Reached download quota"
}}
```