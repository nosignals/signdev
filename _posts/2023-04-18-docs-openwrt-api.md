---
title: Docs Ubus OpenWrt API
tags: [JSON, OpenWrt, Technology, API]
style: 
color: danger
description: Ubus OpenWrt API Reference
---

### 1. Mendapatkan Data dari UBUS Network/Jaringan yang terkoneksi di OpenWrt
Data yang diambil : `MAC, status, statistik interface` dan lainya

Untuk mengambil data bisa menggunakan browser atau pakai `CURL` untuk mendapatkan data, Akses di 
```
http://ipOpenwrt/api/api.php?network=device
```
Contoh hasil data dari API tersebut
<details><summary>Klik Disini</summary>
  
```
"network":{
      "status":true,
      "data":[
         {
            "br-lan":{
               "external":false,
               "present":true,
               "type":"bridge",
               "up":true,
               "carrier":true,
               "auth_status":false,
               "bridge-members":[
                  "eth0"
               ],
               "mtu":1500,
               "mtu6":1500,
               "macaddr":"00:15:18:01:81:31",
               "txqueuelen":1000,
               "ipv6":false,
               "ip6segmentrouting":false,
               "promisc":false,
               "rpfilter":0,
               "acceptlocal":false,
               "igmpversion":0,
               "mldversion":0,
               "neigh4reachabletime":30000,
               "neigh6reachabletime":30000,
               "neigh4gcstaletime":60,
               "neigh6gcstaletime":60,
               "neigh4locktime":99,
               "dadtransmits":1,
               "multicast":true,
               "sendredirects":true,
               "drop_v4_unicast_in_l2_multicast":false,
               "drop_v6_unicast_in_l2_multicast":false,
               "drop_gratuitous_arp":false,
               "drop_unsolicited_na":false,
               "arp_accept":false,
               "statistics":{
                  "collisions":0,
                  "rx_frame_errors":0,
                  "tx_compressed":0,
                  "multicast":0,
                  "rx_length_errors":0,
                  "tx_dropped":0,
                  "rx_bytes":1347973816,
                  "rx_missed_errors":0,
                  "tx_errors":0,
                  "rx_compressed":0,
                  "rx_over_errors":0,
                  "tx_fifo_errors":0,
                  "rx_crc_errors":0,
                  "rx_packets":12915564,
                  "tx_heartbeat_errors":0,
                  "rx_dropped":0,
                  "tx_aborted_errors":0,
                  "tx_packets":8925008,
                  "rx_errors":0,
                  "tx_bytes":39272951715,
                  "tx_window_errors":0,
                  "rx_fifo_errors":0,
                  "tx_carrier_errors":0
               }
            }
         }
      ],
      "error":null
   },
```
</details>


### 2. Mendapatkan Data dari UBUS Network per-Interface
Data yang diambil : `localIP, status, uptime interface, mask localIP` dan lainya

Untuk mengambil data bisa menggunakan browser atau pakai `CURL` untuk mendapatkan data, Akses di 
```
http://ipOpenwrt/api/api.php?network=interfaceYangSupport
```

untuk interface yang support bisa cek di `Terminal` atau `TTYD` dengan format/command
```
ubus list | grep network.interface
```

Contoh hasil data dari API tersebut
<details><summary>Klik Disini</summary>
  
```
{
   "status":true,
   "data":[
      {
         "up":true,
         "pending":false,
         "available":true,
         "autostart":true,
         "dynamic":false,
         "uptime":156,
         "l3_device":"br-lan",
         "proto":"static",
         "device":"br-lan",
         "updated":[
            "addresses"
         ],
         "metric":0,
         "dns_metric":0,
         "delegation":true,
         "ipv4-address":[
            {
               "address":"192.168.1.1",
               "mask":24
            }],
         "ipv6-address":[ ],
         "ipv6-prefix":[ ],
         "ipv6-prefix-assignment":[
            {
               "address":"fdd7:8206:fe3e::",
               "mask":60,
               "local-address":{ }
            }
         ],
         "route":[ ],
         "dns-server":[ ],
         "dns-search":[ ],
         "neighbors":[ ],
         "inactive":{
            "ipv4-address":[ ],
            "ipv6-address":[ ],
            "route":[ ],
            "dns-server":[ ],
            "dns-search":[ ],
			"neighbors":[ ]
			},
         "data":{ }
      }
   ],
   "error":null
}
```
</details>


### 3. Mendapatkan Data dari UBUS informasi dari System
Data yang diambil : `localtime, uptime, cpuload, memory`

Untuk mengambil data bisa menggunakan browser atau pakai `CURL` untuk mendapatkan data, Akses di 
```
http://ipOpenwrt/api/api.php?system=info
```
Contoh hasil data dari API tersebut
<details><summary>Klik Disini</summary>

```
{
   "status":true,
   "data":[{
         "localtime":1675889498,
         "uptime":1270,
         "load":[
            0,
            2656,
            4512
         ],
         "memory":{
            "total":843821056,
            "free":477286400,
            "shared":17694720,
            "buffered":3760128,
            "available":638783488,
            "cached":211587072
         },
         "swap":{
            "total":0,
            "free":0
         }
      }
   ],
   "error":null
}
```
</details>


### 4. Mendapatkan Data dari UBUS informasi System Board atau Device yang dipakai
Data yang diambil : `kernel, device, hostname` dan lainya

Untuk mengambil data bisa menggunakan browser atau pakai `CURL` untuk mendapatkan data, Akses di 
```
http://ipOpenwrt/api/api.php?system=board
```
Contoh hasil data dari API tersebut
<details><summary>Klik Disini</summary>
  
```
{
      "status":true,
      "data":[
         {
            "kernel":"5.4",
            "hostname":"terongWrt",
            "system":"ARMv8 Processor rev 4",
            "model":"Amlogic Meson GXL (S905X) P212 Development Board",
            "board_name":"amlogic,p212",
            "release":{
               "distribution":"OpenWrt",
               "version":"21.02.5",
               "revision":"r16688-fa9a932fdb",
               "target":"armvirt/64",
               "description":"OpenWrt 21.02.5 r16688-fa9a932fdb"
            }
         }
      ],
      "error":null
}
```
</details>


### 5. Mendapatkan Data dari VnStat
Data yang diambil : `network usage`

Untuk mengambil data bisa menggunakan browser atau pakai `CURL` untuk mendapatkan data, Akses di 
```
http://ipOpenwrt/api/api.php?vnstat=Interface
```
Interface = Interface yang tersimpan dalam VnStat kamu seperti `eth0, br-lan, wan0` dan lainya

Contoh hasil data dari API tersebut
<details><summary>Klik Disini</summary>
  
```
{
   "vnstat":{
      "status":true,
      "data":[
         {
            "vnstatversion":"1.18",
            "jsonversion":"1",
            "interfaces":[
               {
                  "id":"eth0",
                  "nick":"eth0",
                  "created":{
                     "date":{
                        "year":2022,
                        "month":7,
                        "day":4
                     }
                  },
                  "updated":{
                     "date":{
                        "year":2023,
                        "month":4,
                        "day":19
                     },
                     "time":{
                        "hour":5,
                        "minutes":21
                     }
                  },
                  "traffic":{
                     "total":{
                        "rx":199985635,
                        "tx":3292880982
                     },
                     "days":[
                        {
                           "id":0,
                           "date":{
                              "year":2023,
                              "month":4,
                              "day":19
                           },
                           "rx":23047,
                           "tx":351322
                        }
                     ],
                     "months":[
                        {
                           "id":0,
                           "date":{
                              "year":2023,
                              "month":4
                           },
                           "rx":10925925,
                           "tx":260103627
                        }
                     ],
                     "tops":[
                        {
                           "id":0,
                           "date":{
                              "year":2023,
                              "month":1,
                              "day":30
                           },
                           "time":{
                              "hour":0,
                              "minutes":0
                           },
                           "rx":2611220,
                           "tx":124756927
                        }
                     ],
                     "hours":[
                        {
                           "id":0,
                           "date":{
                              "year":2023,
                              "month":4,
                              "day":19
                           },
                           "rx":451,
                           "tx":762
                        }
                     ]
                  }
               }
            ]
         }
      ],
      "error":null
   }
}
```
</details>


### 6. Mendapatkan Data dari NetData (hanya untuk mempersingkat)
Data yang diambil : semua data dari netdata

Untuk mengambil data bisa menggunakan browser atau pakai `CURL` untuk mendapatkan data, Akses di 
```
http://ipOpenwrt/api/api.php?netdata=parameter
```
parameter :
- Jika kamu mau mengambil data dari device `Network ETH0`
- kamu dapat mengunakan parameter `net.eth0`, parameter ini sama dengan parameter yang dipakai netdata, contoh : `http://yourip/api/api.php?netdata=net.eth0`
- mendapatkan data **informasi netdata**, bisa dengan parameter `info`, contoh : `http://yourip/api/api.php?netdata=info`
- mendapatkan data **penggunaan sistem/informasi sistem**, bisa dengan parameter `cpu, ram, system` dan lainya, contoh : `http://yourip/api/api.php?netdata=system.cpu`
- **Jika kamu ingin menampilkan semua data, kamu dapat menggunakan fungsi** `data=all`, contoh : `http://yourip/api/api.php?netdata=net.eth0&data=all`

Contoh hasil data dari API Netdata dari `system.cpu`
<details><summary>Klik Disini</summary>
  
```
{
   "netdata":{
      "status":true,
      "data":[
         {
            "labels":[
               "time",
               "guest_nice",
               "guest",
               "steal",
               "softirq",
               "irq",
               "user",
               "system",
               "nice",
               "iowait"
            ],
            "data":[
               [
                  1681857842,
                  0,
                  0,
                  0,
                  0,
                  0,
                  0,
                  0.125,
                  0,
                  1.5
               ]
            ]
         }
      ],
      "error":null
   }
}
```
</details>

### Credits
> - [nosignal](https://github.com/nosignals)
> - [indoWRT](https://www.facebook.com/groups/728998271085718)
> - [DBAI](https://www.facebook.com/groups/421688359852864)
> - GTerongers
