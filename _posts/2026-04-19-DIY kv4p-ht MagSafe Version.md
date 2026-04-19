---
title: DIY kv4p-ht MagSafe Version
date: 2026-04-19 10:10:10 +0800
categories: [Projects]
tags: [kicad, hamradio, kv4p-ht, MagSafe, 3D-Print]
layout: post
toc: true
comments: true
---

### KV4P-HT: Turning Your Android Phone into a Portable Ham Radio

<img width="877" height="671" alt="image" src="https://github.com/user-attachments/assets/fdcfdee2-3ad9-4425-a999-20da6b311bc2" />


KV4P-HT is currently one of the most popular open-source amateur radio projects. It allows your Android phone to function as a portable handheld transceiver (HT). Depending on the RF module selected, it can operate on either the **V-band (144 MHz)** or **U-band (430 MHz)**, but not both at the same time.

The official project provides implementations using off-the-shelf development boards, as well as a custom PCB version designed in KiCad. After dedicating time last year to learning KiCad and completing two practical projects, I have become comfortable designing circuits with it.

Although KV4P-HT does not yet support iOS, many modern Android phones now feature MagSafe-like magnetic attachment. Designing a magnetic version of KV4P-HT would make it much more convenient to attach and detach on the go. Inspired by the sleek MagSafe case from the Meshmastic project, I decided to create my own magnetic enclosure.

Additionally, I found the official KiCad project could be improved in terms of style, organization, and standardization. Therefore, I am refactoring and optimizing it.

**Main Changes in This Revision:**
- Schematic connectivity remains largely unchanged.
- Replaced the USB-to-serial chip from CP2102N to **CH340K** (the original CP2102N is more expensive and harder to hand-solder).
- Improved the schematic drawing style by using local net labels within pages instead of cross-page or global port connections.

**Current Issues:**
1. The PID of the CH340K is not yet supported by the official Android App (Web App works without any problems).
2. The enclosure design is too thick. I plan to switch to a sandwich-style SMA connector to reduce thickness.
3. The 3D model lacks a dedicated slot for the ferrite bead, causing it to protrude significantly and affecting the overall appearance.


[[![](https://www.youtube.com/shorts/y1fTFUp0ZME)](https://youtube.com/shorts/y1fTFUp0ZME?si=IPtniJEnFW-d2lGv)
---


*(Video demonstration will be added later)*
