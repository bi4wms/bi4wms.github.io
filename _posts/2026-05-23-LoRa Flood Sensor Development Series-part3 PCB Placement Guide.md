---
title: LoRa Flood Sensor Development Series - Part 3 PCB Placement Guide
date: 2026-05-23 06:10:10 +0800
categories: [Projects, Lora]
tags: [Lora, Arduino, KiCad, STM32G030, iot]
layout: post
toc: true
comments: true
image: /assets/img/lora-part3.png
---

# LoRa Flood Sensor Development Series – PCB Placement Guide

## Design Overview

We are using an **existing enclosure** for a **shell-fit PCBA design**.

<img width="865" height="865" alt="image" src="https://github.com/user-attachments/assets/7fd44c42-342c-415a-82e0-c59b88a45fc5" />

<img width="865" height="865" alt="image" src="https://github.com/user-attachments/assets/2792f5b1-dbf3-45db-8062-b95e570eb1d1" />



- **Enclosure outer diameter**: 50mm  
- Due to **waterproof design**, the internal space is quite limited.  
- The other side must accommodate a **coin cell battery**, therefore **only single-sided component placement** is allowed.

<img width="865" height="387" alt="image" src="https://github.com/user-attachments/assets/1c9cb851-eec5-4830-bec4-10eb3cfd03ce" />



---

## Step 1: Determine PCBA Outline

1. Locate the **internal PCBA dimension drawing** of the enclosure.
2. Open the drawing with **CAD software** (AutoCAD, DraftSight, etc.).
3. Carefully study the drawing and identify **keep-out areas** (regions where components are prohibited).

<img width="865" height="387" alt="image" src="https://github.com/user-attachments/assets/6feef31d-7b9c-4055-b614-352d97d44a24" />

---

## Step 2: Create Board Outline in KiCad

1. Open your project in **KiCad**.
2. Import the PCBA outline:
   - Go to **File → Import → Graphics** (or use DXF import).
   - Select the prepared dimension file and import it.
3. After import, delete all unnecessary graphics and layers.
4. Keep only the final **PCBA board outline** on the **Edge.Cuts** layer.
<img width="865" height="410" alt="image" src="https://github.com/user-attachments/assets/ecd63b86-9d9b-4efe-9c7f-7e4409be6a5c" />

<img width="865" height="836" alt="image" src="https://github.com/user-attachments/assets/13059c20-76e2-44f2-878a-c27b6d902fe5" />

<img width="865" height="836" alt="image" src="https://github.com/user-attachments/assets/603b8dd0-53d1-443f-b349-3c6de6ce4355" />


---

## Step 3: Component Layout Guidelines

The layout is relatively simple due to single-sided constraints. Follow these rules:

- **Single-sided component placement only**.
- Place **filtering capacitors** as close as possible to the power pins of ICs.
- Arrange components **following the signal flow** direction.
- Position connectors, electrodes, and buttons **exactly** according to the mechanical drawing specifications.
- Pay special attention to **height restrictions** — check component height in limited clearance areas.
- Reserve enough space for the **coin cell battery** on the opposite side.

<img width="865" height="836" alt="image" src="https://github.com/user-attachments/assets/9fa70d05-08aa-490f-a0a6-9b8eb97dff7a" />

---

## 3D Effect Verification

After completing the layout and assigning 3D models in KiCad:
- Use **View → 3D Viewer** to check the overall assembly.
- Verify clearance with the enclosure and coin cell battery.
- Ensure no component interference with the waterproof shell.

<img width="865" height="502" alt="image" src="https://github.com/user-attachments/assets/98c9fb77-86b1-4bb7-8a64-c3c2716cfd56" />


---

## Key Design Principles Summary

- Strictly follow mechanical constraints and keep-out zones
- Prioritize signal integrity and power integrity
- Place decoupling capacitors near power pins
- Maintain sufficient clearance for battery and waterproofing
- Pay attention to component height restrictions
- Optimize component placement according to signal flow

---
