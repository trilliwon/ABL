---
layout: post
title: "Public IP vs Private IP (공인(외부), 내부)"
date: 2018-05-25 16:00:00 +0900
tag: [Computer Science, Network]
---



## Private(Local) IP	vs Public IP (내부 IP, 외부 IP, IP : Internet Protocol)

---

1. Find my IP Address on macOS

---

- `Option + `"**Click Wifi Menu Bar**", then you can see below

![macOS IP]({{ "assets/img/findmacosip.png" | absolute_url }})

- `ipconfig getifaddr en0` if connected via a wireless connection.
- `ipconfig getifaddr en1` if connected via ethernet.
- `ipconfig getifaddr en3` if connected via a Thunderbolt-to-ethernet adaptor.
- `curl http://ipecho.net/plain; echo`

---

# [public-vs-private-ip-address](https://www.iplocation.net/public-vs-private-ip-address)

- **Private IP Address** : Local area 에서 Router 가 사용하는 IP addresses, used to assign computers within your private space without letting them directly expose to the Internet
- **Public IP Address** : Can be accessed over the Internet, globally unique IP address assigned to a computing device

