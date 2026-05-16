---
title: LoRa Flood Sensor Development Series - Part 2 Schematic Design and Component Selection
date: 2026-05-16 06:10:10 +0800
categories: [Projects, Lora]
tags: [Lora, Arduino, KiCad, STM32G030, iot]
layout: post
toc: true
comments: true
image: /assets/img/lora-part2.png
---

# LoRa Flood Sensor Development Series – Complete Schematic Design Guide


Building a reliable, ultra-low-power water leak/immersion detector with LoRa connectivity? This project uses the **STM32G030K8T6** MCU and **SX1278** LoRa module for excellent Arduino compatibility, long-range transmission, and minimal power consumption.

In this guide, we share the full hardware design using the simplest electrode resistance principle for water detection, plus a reserved capacitive sensing option for future upgrades.

---

## Project Overview

**Core Detection Method**: Simple electrode resistance sensing (two electrodes shorted by water).  
**MCU**: STM32G030K8T6 (familiar, well-supported, Arduino-friendly).  
**Wireless**: SX1278 LoRa module (better Arduino ecosystem support than LLCC68).  
**Power**: CR2450 coin cell with large bulk capacitors for LoRa transmission peaks.  
**Programming**: UART bootloader (no SWD required during normal use).

---

## MCU Minimum System Schematic

### Key Features & Connections

- **MCU**: STM32G030K8T6
- **LoRa Interface**: Full SPI connection
- **Programming/Debug**: UART bootloader + serial debugging (simplifies layout by removing SWD)
- **Battery Voltage Monitoring**: Sampled only when **PA13** is driven low (power-saving strategy)
- **Heartbeat LED**: **PB3** drives a status indicator LED
- **Reset Circuit**: Simple RC reset network
- **BOOT0**: Switch for easy bootloader entry during firmware flashing
- **Water Detection**: **PA0** (electrode input, configured as input with internal pull-up)
- **Capacitive Sensing Reserve**: **PB0** and **PB1** pre-wired for future capacitive method evaluation

This minimal system keeps the design compact and low-cost while maintaining flexibility.

<img width="865" height="629" alt="image" src="https://github.com/user-attachments/assets/f2a94e45-2176-47e7-b2b5-6ee8f2dc63e1" />


---

## LoRa RF Module Circuit

We chose the **SX1278** over LLCC68 for superior Arduino library support and easier development.
<img width="865" height="370" alt="image" src="https://github.com/user-attachments/assets/c7dd21da-c110-4ad0-9f75-29ef482d3a7a" />


**Main Features**:
- Standard SPI interface to MCU
- Additional GPIO line connected to MCU for module control (DIO0/DIO1 etc.)
- PI-type matching network on the antenna for optimal RF performance and easy tuning
- Reference design layout followed for maximum range and stability

---

## Water Immersion Detection Circuit (Electrode Resistance Method)

**Principle**: When water bridges the electrodes, it creates a conductive path that triggers the detection signal.
<img width="865" height="629" alt="image" src="https://github.com/user-attachments/assets/1d6991c1-60fc-4172-aa31-05820c4838b6" />


### Circuit Design
- Uses a **PNP + NPN** transistor combination for efficient switching and low standby current.
- **TP** = Detection electrodes (two pairs implemented — one on the front and one on the back of the enclosure for better coverage).
- When water is present → **Q102** turns on → **Q101** turns on → **WATER_DETECT** signal goes **LOW**.
- **MCU Pin**: Configured as input with **pull-up** enabled. Low level = water detected.

This design is extremely simple, reliable, and consumes almost no power when dry.


---

## Reserved Capacitive Water Detection Circuit (Future Upgrade)

For environments where electrode corrosion or false positives from minerals might be an issue, we pre-reserved a **capacitive sensing** path.

<img width="865" height="398" alt="image" src="https://github.com/user-attachments/assets/f59623e4-063e-45d9-ba68-acddd7b6c607" />


**Principle**: Water’s dielectric constant (~80× higher than air) significantly changes the capacitance between two electrodes.

### Circuit Details
- **TP101 & TP102**: Capacitive sensing electrodes (can be PCB traces or custom plates).
- **PWM_OUT**: MCU-generated PWM signal drives the sensing circuit.
- Peak detector formed by diodes and capacitor converts capacitance change into a DC voltage on **CAP_VOLT**.
- MCU can read **CAP_VOLT** via ADC. Significant voltage shift expected when immersed.

This section remains unpopulated by default but gives the hardware future-proofing.

---

## Power Supply Circuit

**Battery**: CR2450 3V coin cell.  
**Challenge**: LoRa transmission can cause high current peaks that may trigger brown-out resets.

<img width="865" height="351" alt="image" src="https://github.com/user-attachments/assets/ee5b42b9-5bad-40fe-95a9-f726c515fffa" />


**Solution**:
- Three **100µF** electrolytic capacitors in parallel as energy storage.
- This bulk capacitance stabilizes voltage during TX bursts, ensuring reliable long-range LoRa operation.

---

## Next Steps

PCB layout

---

*Perfect for smart home, basement monitoring, industrial leak detection, or agriculture applications. Simple, cheap, and long-range thanks to LoRa.*

---

**Tags**: STM32 IoT, LoRa Water Sensor, DIY Leak Detector, Low Power IoT, Water Immersion Sensor, SX1278, Arduino LoRa Project
