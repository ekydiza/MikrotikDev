---
weight: 350
title: "Auto Backup Config"
description: ""
icon: "robot"
date: "2023-08-26T20:43:23+01:00"
lastmod: "2023-08-26T20:43:23+01:00"
aliases:
    - ../guides/hotspot
draft: false
toc: true

---

### Backup dengan type file .backup
```
:local identity [/system identity get name]
:local date [/system clock get date] 
:local time [/system clock get time]
:local day [ :pick $date 4 6 ]
:local month [ :pick $date 0 3 ]
:local year [ :pick $date 7 11 ]

:local months {"jan"="01";"feb"="02";"mar"="03";"apr"="04";"may"="05";"jun"="06";"jul"="07";"aug"="08";"sep"="09";"oct"="10";"nov"="11";"dec"="12"}
:local monthr {"jan";"feb";"mar";"apr";"may";"jun";"jul";"aug";"sep";"oct";"nov";"dec"}

:set month ($months->$month)
:set time ( [:pick $time 0 2].[:pick $time 3 5].[:pick $time 6 8] )

:local filename "$identity-$year$month$day-$time"
:put $filename

/system backup save name=$filename
:delay 15s
/tool e-mail send to="email@gmail.com" subject="Backup Router" body="File backup ini dikirim secara otomatis via email" file="$filename.backup" start-tls=yes
:delay 15s
/file remove $filename
```

<p></p>

### Backup dengan type file .rsc
```
:local identity [/system identity get name]
:local date [/system clock get date] 
:local time [/system clock get time]
:local day [ :pick $date 4 6 ]
:local month [ :pick $date 0 3 ]
:local year [ :pick $date 7 11 ]

:local months {"jan"="01";"feb"="02";"mar"="03";"apr"="04";"may"="05";"jun"="06";"jul"="07";"aug"="08";"sep"="09";"oct"="10";"nov"="11";"dec"="12"}
:local monthr {"jan";"feb";"mar";"apr";"may";"jun";"jul";"aug";"sep";"oct";"nov";"dec"}

:set month ($months->$month)
:set time ( [:pick $time 0 2].[:pick $time 3 5].[:pick $time 6 8] )

:local filename "$identity-$year$month$day-$time"
:put $filename

/export file=$filename
:delay 15s
/tool e-mail send to="email@gmail.com" subject="Backup Router" body="File backup ini dikirim secara otomatis via email" file="$filename.rsc" start-tls=yes
:delay 15s
/file remove $filename
```

<p></p>

### How to use
