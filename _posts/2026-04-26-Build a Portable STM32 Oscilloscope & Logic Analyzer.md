---
title: How to Build a DIY STM32 Oscilloscope (Step-by-Step Guide)
date: 2026-04-26 10:10:10 +0800
categories: [Projects, Oscilloscope]
tags: [Oscilloscope, Logic Analyzer, Altium, STM32F103CBT6, 3D-printed]
layout: post
toc: true
comments: true
---

# A Compact STM32-Based Multifunction Instrument (Oscilloscope + Logic Analyzer + More)

[![Watch Demo Video](https://img.youtube.com/vi/id5blkNelKI/0.jpg)](https://youtube.com/shorts/id5blkNelKI?feature=share)
<!-- 点击图片可跳转到 YouTube 视频 -->

🎥 **PCBA and 3D printed case:**  

<img width="865" height="525" alt="image" src="https://github.com/user-attachments/assets/3460a333-18ea-4a40-83d8-9b5ba97710c1" />



There is a very popular multifunction oscilloscope project on GitHub that uses an STM32 development board. With just a few Dupont wires and a USB cable, it can be turned into a versatile instrument featuring:

- Oscilloscope  
- Logic analyzer  
- Voltmeter  
- Counter  
- PWM signal generator  

The project also provides a Qt-based desktop application that supports **Windows, Linux, and macOS**, making it truly cross-platform.

🔗 Original project:  

[EMBO Scope](https://github.com/bi4wms/MiniMultiScope)

---

## 🚀 My Hardware Implementation

🔗 **Project repository:**  

[BI4WMS Scope Hardeware](https://github.com/bi4wms/MiniMultiScope)

To improve usability, I designed a **dedicated hardware version** of this project.

---

## Motivation

While the original project is powerful, it has one major limitation:

> It is designed only for generic development boards and lacks dedicated hardware.

This significantly affects usability and limits its broader adoption.

To address this, I designed a **custom hardware solution**, including:

- A dedicated PCB  
- A compact 3D-printed enclosure  
- Custom silkscreen labeling  

---

## Hardware Design

The design is based on the widely used **STM32F103C8T6**, which is also used in my integrated SimpleFOC project.

<img width="865" height="678" alt="image" src="https://github.com/user-attachments/assets/8dbbecd9-b8bc-4e10-bd33-0a7c74f64e74" />



The firmware implementation is relatively straightforward, mainly leveraging:

- ADC (for voltage sampling)  
- Timer peripherals (for signal generation and measurement)  
- GPIO (for logic analysis and control)  

### Pin Mapping

Following the original Blue Pill (STM32F103C8T6) design:

| Function                     | Pins              |
|----------------------------|------------------|
| Oscilloscope / Voltmeter   | PA1, PA2, PA3    |
| Logic Analyzer             | PA1, PA2, PA3    |
| Counter                    | PA8              |
| PWM Generator              | PA15, PB6        |

---

## Schematic Design


<img width="865" height="389" alt="image" src="https://github.com/user-attachments/assets/e5579fe0-bba7-4044-9bb5-61fa7ddb4872" />


The schematic is built around a **minimal STM32F103C8T6 system**, with all required pins broken out for easy access.

---

## PCB Design

TOP
<img width="865" height="463" alt="image" src="https://github.com/user-attachments/assets/c3e18c2e-faf8-4114-9b92-cd86b9d05395" />

BOTTOM
<img width="865" height="487" alt="image" src="https://github.com/user-attachments/assets/aff6289c-b6e4-4a65-9df3-5f93b2997624" />


Given the simplicity of the circuit, a **2-layer PCB** is sufficient.

- 📏 Size: **42 mm × 22 mm**  
- Compact and enclosure-friendly  

---

## 3D PCBA

<img width="865" height="511" alt="image" src="https://github.com/user-attachments/assets/ea99b211-2c13-4fe9-be2a-ab02f43b39eb" />


A full 3D model of the assembled PCB was created to verify mechanical compatibility with the enclosure.

---

## IBOM (Interactive BOM)

An interactive BOM was generated to simplify assembly and component identification.

<img width="865" height="435" alt="image" src="https://github.com/user-attachments/assets/18130ce8-4cd8-431c-8838-310886c864f2" />



---

## Enclosure & Silkscreen

<img width="865" height="525" alt="image" src="https://github.com/user-attachments/assets/7a69e99d-6866-4e45-983d-0319e45c82a9" />


The enclosure and silkscreen graphics were designed using **JLCEDA**:

- Custom-fit enclosure  
- Clear interface labeling  
- Much better usability than bare development boards  

---

## Usage

<img width="865" height="384" alt="image" src="https://github.com/user-attachments/assets/b90b4563-8e21-49cd-aec7-b642a0042b74" />


The device connects directly to a PC via a **USB Type-C cable**.

### Steps

1. Connect the device to your computer  
2. Launch the desktop application  
3. Select the corresponding serial port  
4. Start using the instrument  

The UI is intuitive and easy to understand.

---

## Software

The desktop application is built with **Qt**, offering:

- Cross-platform support  
- Real-time waveform display  
- Easy interaction with all functions  

---

## Resources

All files are available in the GitHub repository:

- Gerber files  
- Pick-and-place files  
- BOM  
- 3D enclosure files  
- Silkscreen files  

🔗 Repository:  
[BI4WMS Scope Hardware](https://github.com/bi4wms/MiniMultiScope) 

---

## Conclusion

This project transforms a development-board-based tool into a **compact, integrated, and user-friendly multifunction instrument**.

It demonstrates how open-source projects can be extended with custom hardware to significantly improve real-world usability.

---

⭐ If you find this project useful, feel free to star the repository or contribute!
