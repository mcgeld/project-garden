---
id: juggling-vfx
title: Sync-Juggling VFX System
status: seed            # options: seed, active, dormant, archived
tags: [python, opencv, esp32, hardware, vfx]
created: 2026-01-20
budget_est: $50
feasibility: High
---

# 💡 Vision
A juggling system where balls light up in perfect synchronization with a music track. 
**Phase 1 (Software):** A desktop app that uses Computer Vision to overlay light effects on a video of me juggling "proxy" balls.
**Phase 2 (Hardware):** Physical balls with ESP32-C3 chips that receive time-code data via ESP-NOW.

# 🔬 Research & Tech Stack

## Phase 1: The "Studio" (MVP)
* **Language:** Python
* **Core Lib:** OpenCV (`cv2`)
* **Logic:** * Track 3 distinct colored balls (Red, Green, Blue) in an MP4 video.
    * Map their (x,y) coordinates to a timeline.
    * Render "Glow" effects over the coordinates based on a JSON light script.
* **Advantage:** Zero cost. Allows perfect syncing of routine to music before hardware exists.

## Phase 2: The Hardware
* **Microcontroller:** Seeed Studio XIAO ESP32-C3 (Tiny, battery charge support).
* **Protocol:** **ESP-NOW**. 
    * *Topology:* PC -> Serial -> Bridge Dongle -> Wireless Broadcast -> Balls.
    * *Why:* "Connectionless" Wi-Fi. Lower latency than Bluetooth, simpler than standard Wi-Fi.
* **Power:** 14500 Li-Ion (AA size, 3.7V). Center-mounted for weight balance.
* **Shell:** Bambu P1S printed TPU. 0% walls, 15% Gyroid infill for diffusion and durability.

# 🚧 Blockers & Next Steps
* [ ] **Constraint:** Currently in "saving mode" (Budget: $0). Focus on Phase 1.
* [ ] **Action:** 3D print 3 "proxy balls" in matte PLA (Red, Green, Blue) weighted to match final hardware.
* [ ] **Action:** Record 10s test video.