---
id: synch-juggling-vfx
title: Music Synced Juggling Balls
status: seed
tags: [esp32, esp-now, led, hardware, python]
created: 2026-02-04
budget_est: $100 (Prototype Phase)
feasibility: High
---

# 💡 Vision
A set of juggling balls that synchronize lighting patterns to music.
* **The Problem:** Existing props rely on rigid, pre-set patterns or unreliable Bluetooth.
* **The Solution:** A "Timecode" system where a PC broadcasts the song position via ESP-NOW to all balls simultaneously.
* **The workflow:** I load an MP3 into a custom desktop app -> Design the light show -> "Compile" the show to the balls -> Perform.

# 🔬 Research & Tech Stack
### The Architecture
* **Topology:** Bridge Mode. PC -> USB Serial -> "Commander" ESP32 -> ESP-NOW Broadcast -> Juggling Balls.
* **Protocol:** **ESP-NOW**. Connectionless Wi-Fi. Extremely low latency (<10ms) and high reliability compared to BLE.

### The Hardware BOM (Bill of Materials)
* **The Brain (Ball):** **Seeed Studio XIAO ESP32-C3** (or "SuperMini" form factor). Tiny, cheap.
* **The Brain (Commander):** **ESP32-S3 Mini** with **External Antenna** (IPEX/uFL connector) for range reliability.
* **The Power:** **14500 Li-Ion Battery (3.7V)**.
    * *Spec:* **Pre-wired / No Connector** (Saves space vs battery holder).
    * *Capacity:* ~500mAh (good for 1-1.5hrs).
    * *Warning:* Do not use 18650s (too big) or Coin Cells (too weak).
* **The Charging:** **TP4057 Module** (USB-C).
    * *Why:* Smaller than TP4056, has reverse polarity protection.
    * *Critical:* Must use **500mA version** (or swap resistor) to prevent overheating the battery.
* **The Light:** **WS2812B LED Strip (144 LEDs/m)**.
    * *Spec:* **IP30** (Non-waterproof). Cut into small segments to wrap around the core.
* **The Shell:** 3D Printed **TPU (95A)**. Transparent/Clear. 0% Walls, Gyroid Infill for diffusion.

### The Software (MVP)
* **Language:** Python (for the desktop sequencer).
* **Video POC:** Use OpenCV to track colored "proxy" balls in a video and overlay digital effects to test the concept before buying hardware.

# 🚧 Blockers & Next Steps
* [ ] **Financial:** Waiting for budget to replenish (~$100 target).
* [ ] **Action:** Build the "Video POC" (Computer Vision version) first since it costs $0.
