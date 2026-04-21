---
title: “KV4P HT DIY Guide: Add MagSafe Mount for Android Ham Radio”
date: 2026-04-19 10:10:10 +0800
categories: [Projects]
tags: [kicad, hamradio, kv4p-ht, MagSafe, 3D-Print]
layout: post
toc: true
comments: true
---

# KV4P HT DIY Guide: Add MagSafe Mount for Android Ham Radio

All design files can be found in my github

[KV4P-HT-MagSafe](https://github.com/bi4wms/kv4p-ht-MagSafe)


<img width="877" height="671" alt="image" src="https://github.com/user-attachments/assets/fdcfdee2-3ad9-4425-a999-20da6b311bc2" />

## What is KV4P HT?

KV4P HT is an open-source DIY project that turns an Android phone into a portable ham radio transceiver. It connects hardware and software to enable radio communication directly from your smartphone.

KV4P-HT is currently one of the most popular open-source amateur radio projects. It allows your Android phone to function as a portable handheld transceiver (HT). Depending on the RF module selected, it can operate on either the **V-band (144 MHz)** or **U-band (430 MHz)**, but not both at the same time.

The official project provides implementations using off-the-shelf development boards, as well as a custom PCB version designed in KiCad. After dedicating time last year to learning KiCad and completing two practical projects, I have become comfortable designing circuits with it.

## Why Add a MagSafe Mount?

Adding MagSafe improves usability:

Easier mounting on phone
Better portability
Cleaner setup
Quick attach/detach

Although KV4P-HT does not yet support iOS, many modern Android phones now feature MagSafe-like magnetic attachment. Designing a magnetic version of KV4P-HT would make it much more convenient to attach and detach on the go. Inspired by the sleek MagSafe case from the Meshmastic project, I decided to create my own magnetic enclosure.

<img width="865" height="662" alt="image" src="https://github.com/user-attachments/assets/4723d463-9355-406a-aece-3809a6acef4c" />


Additionally, I found the official KiCad project could be improved in terms of style, organization, and standardization. Therefore, I am refactoring and optimizing it.

<img width="865" height="581" alt="image" src="https://github.com/user-attachments/assets/a79f3f93-f570-49f7-b00f-d13aab5a4a55" />

<img width="1089" height="649" alt="image" src="https://github.com/user-attachments/assets/814df652-de5c-4904-8342-60dc8563e53b" />

<img width="1124" height="603" alt="image" src="https://github.com/user-attachments/assets/c9d55291-d3e8-403d-b93a-479452ba2d3e" />


## Materials and Tools Needed

列清单（非常重要）：

KV4P HT board
MagSafe magnet ring
Power components
3D printed case (if any)
Tools (soldering iron, etc.)

**Main Changes in This Revision:**
- Schematic connectivity remains largely unchanged.
- Replaced the USB-to-serial chip from CP2102N to **CH340K** (the original CP2102N is more expensive and harder to hand-solder).
- Improved the schematic drawing style by using local net labels within pages instead of cross-page or global port connections.

**Current Issues:**
1. The PID of the CH340K is not yet supported by the official Android App (Web App works without any problems).
2. The enclosure design is too thick. I plan to switch to a sandwich-style SMA connector to reduce thickness.
3. The 3D model lacks a dedicated slot for the ferrite bead, causing it to protrude significantly and affecting the overall appearance.

[![Watch the video](https://img.youtube.com/vi/y1fTFUp0ZME/0.jpg)](https://youtube.com/shorts/y1fTFUp0ZME)


