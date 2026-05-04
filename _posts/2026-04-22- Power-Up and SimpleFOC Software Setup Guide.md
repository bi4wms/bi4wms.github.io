---
title: SimpleFOC Integrated Board from Zero to One - Part 3
date: 2026-04-22 6:10:10 +0800
categories: [Projects, Simplefoc]
tags: [Simplefoc, Arduino, Altium, STM32F103CBT6, Motor]
layout: post
toc: true
comments: true
image: /assets/img/simplefoc-part3.png
---

**SimpleFOC Integrated Board Hardware Practice: From Zero to One (3) – Power-Up and SimpleFOC Software Setup Guide**

# BI4WMS FOC Driver Board - Power-Up and SimpleFOC Software Setup Guide

### Board Preparation

Solder the components onto the PCB according to the IBOM (Interactive Bill of Materials).
<img width="865" height="435" alt="image" src="https://github.com/user-attachments/assets/0ef1415e-7911-49c2-869e-1d1338c1f5b2" />


**Key components should be soldered first.**
<img width="865" height="426" alt="image" src="https://github.com/user-attachments/assets/3221b96f-97f8-4660-9e82-1619d11b287b" />


Use a multimeter to check the power rails for any short circuits. Once there is no short circuit detected, power the board using a regulated DC power supply with current limiting enabled. Measure the 3.3V output.

If the 3.3V output is normal and the power indicator LED lights up, it indicates that the basic power-up functionality of the circuit board is working correctly. Next, we will prepare the software environment.

<img width="865" height="442" alt="image" src="https://github.com/user-attachments/assets/9ab72c98-b96d-452f-bd73-5351bfacd263" />


## SimpleFOC Software Debugging Environment Setup

### 1. Install Arduino IDE
Download and install the Arduino IDE from the official website. The classic **1.8.x** version is recommended.

### 2. Configure STM32 Support in Arduino IDE

#### 2.1 Add STM32 Core
Go to **File → Preferences**, and in the **Additional Boards Manager URLs** field, add the following link:
https://github.com/stm32duino/BoardManagerFiles/raw/main/package_stmicroelectronics_index.json

<img width="865" height="490" alt="image" src="https://github.com/user-attachments/assets/48227560-6b87-4fcb-b4df-353adc513d97" />


#### 2.2 Install STM32 Boards
Go to **Tools → Board → Boards Manager**, search for **STM32**, and install the **STM32** series development board package.
<img width="865" height="501" alt="image" src="https://github.com/user-attachments/assets/97f38e69-ae7f-405e-98dc-4c45ece5e8eb" />



#### 2.3 Install STM32CubeProgrammer
Download **STM32CubeProgrammer** from the official ST website and install it with the default settings.

#### 2.4 Test STM32 Arduino Configuration
Open any STM32 example sketch in the Arduino IDE.  

Press and hold the **BOOT0** button on the driver board, then connect the Type-C cable to power on the board (this enters bootloader mode).  
<img width="865" height="525" alt="image" src="https://github.com/user-attachments/assets/96f154f2-a0b9-451a-9a95-9a86b9bdf6e7" />


Compile and upload the sketch directly from the Arduino IDE.

> **Note**: The hardware design utilizes the STM32 built-in bootloader with UART download functionality. Since the board has an integrated USB-to-UART chip, firmware can be flashed using only a single Type-C cable.

You can also generate the binary file after compilation and upload it using **STM32CubeProgrammer** in UART (serial) mode. If the upload completes successfully, it confirms that the board's programming function is working normally.
<img width="865" height="657" alt="image" src="https://github.com/user-attachments/assets/a0e67513-04ce-49d8-87ef-5a3387f10cc2" />


### 3. Install SimpleFOC Library
Install the library using Arduino IDE’s Library Manager:

- Go to **Sketch → Include Library → Manage Libraries**
- Search for **SimpleFOC**
- Install the **SimpleFOC** library
<img width="865" height="479" alt="image" src="https://github.com/user-attachments/assets/55f1f4a5-a8ee-4942-8a01-d97c7537afd3" />

<img width="865" height="464" alt="image" src="https://github.com/user-attachments/assets/dd0432f5-7a16-4c67-aad4-3d78efb2e93d" />


### 4. Test the BI4WMS FOC Driver Kit

Use the official test code from the SimpleFOC library. If it compiles successfully, the library has been installed correctly.

Example codes can be found in the Arduino IDE under:  
**File → Examples → SimpleFOC**

### 5. Board Testing

Use the **bluepill_position_control** example. Modify the magnetic sensor and DRV8313 driver configurations according to your hardware. The example can be downloaded directly from GitHub.

https://raw.githubusercontent.com/bi4wms/SimpleFOC/refs/heads/main/bi4wmsFOC.ino

1. Press and hold the **BOOT0** button, then connect the Type-C cable to power the board.
2. Compile and upload the firmware.
3. Supply **12V** power to the motor.
4. Once initialization is complete, open the **Serial Monitor** and send commands to control the motor.

<img width="865" height="593" alt="image" src="https://github.com/user-attachments/assets/f90cd2b3-1bc7-489c-af5d-525e96bff6b6" />

<img width="865" height="634" alt="image" src="https://github.com/user-attachments/assets/72c7b201-e4c4-4ac8-8423-1cab4a980b42" />


<img width="540" height="613" alt="image" src="https://github.com/user-attachments/assets/aa4b1103-c358-497d-9aab-002adcad4533" />


For a complete list of interaction commands and detailed usage instructions, please refer to the official SimpleFOC documentation.

---

**Next Article:** We will analyze and explain the specific SimpleFOC example code in detail.
