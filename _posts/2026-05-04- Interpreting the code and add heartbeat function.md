---
title: SimpleFOC Integrated Board from Zero to One - Part 4
date: 2026-05-04 16:10:10 +0800
categories: [Projects, Simplefoc]
tags: [Simplefoc, Arduino, Altium, STM32F103CBT6, Motor]
layout: post
toc: true
comments: true
image: /assets/img/simplefoc-part4.png
---

**SimpleFOC Integrated Board Hardware Practice: From Zero to One (4) – Interpreting the Code and add heartbeat function**

### Interpreting the Code

This article mainly explains the code.  
The example is based on the official **SimpleFOC** example: `full_control_serial.ino`.

### Main Modifications

1. **Power supply**
2. **DRV8313 driver chip control pins**
3. **Motor pole pair parameters** (different brushless motors have different numbers of pole pairs)
4. **Magnetic encoder related settings**

After completing the modifications, upload the code and test it using serial commands.

---

### Adding a Heartbeat Indicator

When designing hardware circuits, in addition to the power supply indicator LED, a **heartbeat indicator LED** is typically added to indicate that the software system is running normally. This design is no exception.

Most beginner Arduino projects use `delay()` to blink an LED. However, when using the **FOC (Field Oriented Control)** vector control algorithm for the motor, using `delay()` becomes very inappropriate. Using Arduino’s FreeRTOS would also consume too many system resources.

After research, the `millis()` function can be used to achieve a non-blocking heartbeat LED. The key code is as follows:

**Variable and function declarations for the heartbeat:**

```cpp
// (Add your variable declarations here)