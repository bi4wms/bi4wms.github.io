---
title: Collaborating to Build a Hardware IoT Device – Part 1 Water Immersion Sensor System Solution
date: 2026-05-10 16:10:10 +0800
categories: [Projects, Lora]
tags: [Lora, Arduino, KiCad, STM32G030, iot]
layout: post
toc: true
comments: true
image: /assets/img/lora-part1.png
---

# Collaborating to Build a Hardware IoT Device – Water Immersion Sensor System Solution

Recently, I evaluated a water immersion sensor system solution. Here is a quick summary of the proposed design.

## 1. User Requirements

Design a wearable water immersion alarm device. The key requirements are as follows:

1. The device must be wearable, powered by a coin cell battery, and support standby operation for more than 1 year.
2. In a dry environment, the device remains in standby mode. When water is detected, it immediately transmits an RF signal and reports a unique identity code to the platform system.
3. The system must support a capacity of **500 devices**.
4. Communication range must exceed **200 meters**.

## 2. System Solution

With coin cell battery power and a standby time of over 1 year, **ultra-low power consumption** is the top priority. At the same time, supporting 500 devices makes ordinary RF solutions difficult to implement reliably. We need a protocol stack that supports reliable addressing, collision avoidance, retransmission, and acknowledgments.

After evaluation, the **LoRa system solution** is the most suitable choice.

- **Node Device Side**: Use a mature LoRa chipset such as **SX1278 + low-power MCU**.
- **Water Detection**: Adopt the proven resistance-based detection method, with special attention to electrode anti-corrosion design.

I have become proficient with KiCad recently. After selecting a suitable off-the-shelf enclosure, I completed the PCB layout design to fit inside the shell.

**3D PCBA Appearance**

*(Insert 3D PCBA rendering image here)*

I then fed the 3D PCBA images, enclosure photos, and key product information into an AI tool to generate a promotional color flyer for the node device.

**System Platform Architecture**

The platform adopts a **LoRa Gateway + PC Platform** solution. The LoRa gateway communicates with the PC system via wired or wireless networks. I also used AI to generate the overall system design block diagram.

---

**Next Article**: Schematic design – stay tuned!

---

*Technical Blog Post – Water Immersion Sensor Project*