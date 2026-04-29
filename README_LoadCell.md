# Load Cell Based Food Dispensing System

A commercial-grade precision weighing system designed for food dispensing applications, built from scratch using Arduino UNO, a 24-bit ADS1231 ADC, and a custom PCB designed in EasyEDA.

---

## Overview

This project implements a fully calibrated, real-time weighing system capable of accurately measuring dispensed food quantities. The system was designed with commercial deployment in mind — prioritizing noise immunity, signal integrity, and long-term reliability over off-the-shelf breakout board solutions.

---

## Features

- ✅ 24-bit precision ADC (ADS1231 by Texas Instruments) — 13nV RMS noise
- ✅ Real-time serial data acquisition at high resolution
- ✅ Software tare function (zero offset)
- ✅ Multi-point calibration routine
- ✅ Software averaging filter for stable readings
- ✅ Custom PCB with dedicated ground plane for EMI shielding
- ✅ Zero DRC errors — complete 40/40 net routing
- ✅ GX16 aviation connectors with shielded twisted pair cable for robust load cell interfacing
- ✅ Fully calibrated and tested

---

## Hardware Components

| Component | Details |
|-----------|---------|
| Microcontroller | Arduino UNO (ATmega328P) |
| ADC | ADS1231 — 24-bit, Texas Instruments |
| Load Cell | Strain gauge type |
| Connector | GX16 aviation connector |
| Cable | Shielded twisted pair |
| PCB | Custom designed in EasyEDA |
| Power Supply | 5V regulated |

---

## Why ADS1231?

Most load cell interfaces rely on HX711 (24-bit) which is commonly available but has limitations in noise performance and long-term commercial availability. The **ADS1231** was chosen for:

- Superior noise performance: **13nV RMS** input-referred noise
- Designed specifically for weigh-scale applications
- Better long-term commercial availability for production deployments
- Internal oscillator — reduces external component count

---

## PCB Design Highlights

- Designed using **EasyEDA**
- Dedicated **ground plane** for EMI shielding and signal integrity
- Careful trace routing to minimize noise coupling near the ADC input
- **Zero DRC errors** on final layout
- Complete **40/40 net routing** — no unconnected nets

---

## Firmware Overview

The embedded firmware is written in **Embedded C** for Arduino UNO and handles:

1. **24-bit serial data acquisition** from ADS1231 via bit-banged SPI
2. **Tare function** — stores offset at startup or on button press
3. **Software averaging filter** — averages N samples for stable output
4. **Calibration routine** — maps raw ADC counts to weight in grams using known reference weights

---

## Repository Structure

```
load-cell-food-dispenser/
│
├── firmware/
│   └── load_cell_main.ino        # Main Arduino firmware
│
├── pcb/
│   ├── schematic.json            # EasyEDA schematic file
│   ├── pcb_layout.json           # EasyEDA PCB layout file
│   └── gerber/                   # Gerber files for fabrication
│
├── docs/
│   ├── circuit_diagram.png       # Circuit diagram
│   └── block_diagram.png         # System block diagram
│
└── README.md
```

---

## How to Use

### Hardware Setup
1. Connect load cell to ADS1231 differential inputs (INA+, INA−)
2. Use shielded twisted pair cable and GX16 connectors for the load cell interface
3. Connect ADS1231 data and clock pins to Arduino as defined in firmware
4. Power the system with a stable 5V supply

### Firmware Upload
1. Open `firmware/load_cell_main.ino` in Arduino IDE
2. Select **Board:** Arduino UNO
3. Select the correct **COM port**
4. Click **Upload**
5. Open Serial Monitor at **9600 baud** to view readings

### Calibration
1. Place no load on the scale → press tare button (or reset)
2. Place a known weight (e.g. 100g) on the scale
3. Update the calibration factor in firmware and re-upload
4. System is ready for use

---

## Results

- Stable weight readings with < ±1g variation after averaging
- Tare and calibration working accurately across multiple test cycles
- PCB performed with no noise issues — ground plane effectively isolated ADC inputs
- System fully calibrated and tested with known reference weights

---

## Tools Used

| Tool | Purpose |
|------|---------|
| EasyEDA | PCB schematic and layout design |
| Arduino IDE | Firmware development and upload |
| Embedded C | Firmware language |
| Serial Monitor | Real-time weight output debugging |

---

## Author

**Prathyum G**  
B.Tech – Electrical & Electronics Engineering  
University Visvesvaraya College of Engineering (UVCE), Bangalore  
📧 prathyum14@gmail.com
