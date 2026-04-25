---
title: SimpleFOC Integrated Board Hardware in Practice-From zero to one
date: 2026-04-25 10:10:10 +0800
categories: [Projects, Simplefoc]
tags: [Simplefoc, Arduino, Altium, STM32F103CBT6, Blushless motor]
layout: post
toc: true
comments: true
---

## Why Do We Need a Tail-Mounted SimpleFOC Integrated Board?

As the title suggests, this is a **from-zero-to-one series** covering hands-on learning, design, debugging, and practical insights. The series walks through:

* Hardware design fundamentals
* Software and hardware environment setup
* Getting the motor spinning
* Applying it to real-world projects

This is a record of my journey learning **SimpleFOC**, aimed at helping beginners quickly understand, design, and build their own motor control boards and applications.

---

## Final Result Preview

* Mounted on a **4010 brushless motor**
<img width="865" height="417" alt="image" src="https://github.com/user-attachments/assets/910bd015-2a9b-43ad-90d2-f90838f4ee7e" />


* Mounted on a **2204 brushless motor**

<img width="865" height="314" alt="image" src="https://github.com/user-attachments/assets/4f2d9b40-72d5-4333-b6d0-72097d29928a" />


*Control demo video:*

[![Demo Video](https://img.youtube.com/vi/-CYr3gOOTzE/0.jpg)](https://youtube.com/shorts/-CYr3gOOTzE)

---

## 1. What is SimpleFOC?

**SimpleFOC (Simple Field Oriented Control)** is a popular open-source project that makes it easy to implement **Field Oriented Control (FOC)** for brushless motors.

Compared to traditional trapezoidal (square wave) control, FOC offers:

* Smoother and quieter operation
* Higher torque output
* Better efficiency

It is widely used in applications such as:

* Robotics
* Gimbals
* Self-balancing vehicles

For many makers, SimpleFOC is often the first step into advanced motor control.

Compared to other open-source FOC platforms like VESC or ODrive, **SimpleFOC is more beginner-friendly**, mainly because:

* It provides a simple and intuitive **Arduino library**
* It leverages the rich Arduino ecosystem
* It significantly lowers the barrier to entry

With just basic programming knowledge, users can quickly implement:

* Velocity control
* Position control
* Torque control

---

## 2. Limitations of Official SimpleFOC Development Boards

The official SimpleFOC boards (such as the Shield and Mini) are great for learning and prototyping. They are affordable, open-source, and easy to use.

However, when transitioning from experimentation to real-world applications, several issues become apparent:

* **Large size and lack of compactness**
* **Difficult to mount directly on motors**, requiring many jumper wires
* **Messy wiring**, which is prone to loosening and instability
* **Closed-loop control is cumbersome**, often requiring external encoders and manual alignment
* **Low integration**, leading to complex assembly and debugging

These limitations can be frustrating, especially for beginners trying to build compact and reliable systems.

---

## 3. Why Design a Tail-Mounted SimpleFOC Integrated Board?

To address these pain points, I designed a **compact, highly integrated SimpleFOC control board** that can be mounted directly on the motor.

This board is specifically created for beginners and makers who want a **clean, compact, and practical solution**.

### Key Features

#### 🔧 Direct Motor Mounting

* Slot-based PCB design
* Compatible with **2204–4010 brushless motors**
* Can be mounted directly on the motor base
* Adds almost no extra volume

#### 🧲 Onboard Magnetic Encoder

* Sensor placed at the center of the PCB
* Perfectly aligned with motors using magnetic rings
* For motors without a magnet: simply attach a small magnet to the shaft
* Enables **high-precision closed-loop control** with minimal setup

#### 🔌 USB Type-C Interface

* Built-in USB-to-serial chip
* One Type-C cable for:

  * Firmware upload
  * Parameter tuning
  * Real-time debugging

#### 🔗 Flexible Expansion

* Independent UART control
* External I2C sensors
* Support for ABZ encoders

#### ⚡ Complete Hardware Integration

* Built-in current sensing resistors
* **DRV8313 motor driver** onboard
* Supports current loop control
* Suitable for small to medium power motors

#### 🧠 Main Controller

* **STM32F103CBT6 microcontroller**
* Rich peripherals and widely supported

#### 📐 Physical Specs

* 42mm × 42mm circular PCB
* 4-layer PCB design

#### 🌐 Fully Open Source

* Hardware and software fully open
* Includes:

  * Altium design files
  * Manufacturing (PCBA) files
  * Arduino-based reference firmware

---

## 4. Summary

With this integrated board, you no longer need to worry about:

* Complex wiring
* Mounting difficulties
* Tedious setup procedures

Simply:

1. Mount the board
2. Attach a magnet (if needed)
3. Connect power

…and you can immediately start working with **SimpleFOC**.

This makes it especially suitable for anyone looking to build **compact, clean, and high-performance motor control systems**.

---

## What’s Next?

In the next article, we’ll dive deep into the **hardware design details** of this board, including:

* Schematic analysis
* Component selection
* PCB layout design

Stay tuned!
