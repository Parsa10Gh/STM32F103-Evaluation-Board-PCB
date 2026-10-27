# STM32F103RET6 Evaluation Board - Hardware & PCB Design

A custom 2-layer Printed Circuit Board (PCB) and hardware schematic design for an **ARM Cortex-M3 (STM32F103RET6)** development and evaluation board, designed in **Altium Designer**. 

This project encompasses the complete hardware design lifecycle: component selection based on datasheet specifications, schematic capture, footprint verification, 2-layer PCB layout, and Design Rule Checking (DRC) for manufacturability.

## Project Status

- **Schematic design:** Completed
- **PCB layout:** Completed
- **Physical fabrication:** Not performed
- **Hardware testing:** Not performed

This repository documents the electronic design work completed as part of an undergraduate engineering course. The physical board has not been fabricated or experimentally validated.

## 🔧 Key Hardware Features

* **Microcontroller:** STMicroelectronics **STM32F103RET6** (ARM 32-bit Cortex-M3 CPU, LQFP-64 package).
* **Clock System:**
  * **HSE (High-Speed External):** 8 MHz HC-49US crystal oscillator paired with 18 pF ceramic load capacitors.
  * **LSE (Low-Speed External):** 32.768 kHz crystal for internal RTC.
* **Power Supply Architecture:**
  * **12V DC Barrel Jack Input:** Stepped down to 5V using an **LM78M05** linear voltage regulator with input/output decoupling (0.33 µF and 0.1 µF).
  * **5V USB Bus Power:** Direct 5V power supply option via the USB Type-C connector with ferrite bead EMI filtering.
* **USB-to-UART Bridge:** Onboard **FT232RL** (SSOP-28) converter connected to a USB Type-C port, featuring TX/RX status indicator LEDs.
* **User Peripherals & I/O:**
  * **3x User Push Buttons** (SMD 3×6×2.5 mm).
  * **1x Reset Push Button (NRST)** with 0.1 µF parasitic reset protection capacitor and pull-up network.
  * **Boot Mode Selection Circuit** (Switch-controlled BOOT pin configuration).
  * **5V Piezo Buzzer** (`AI-1223-TWT-5V-R`) driven by a **BC817** NPN SMD transistor.
  * **SMD 1210 User & Status LEDs** with transistor driver and current-limiting resistors.
* **Expansion & Debugging:**
  * Dedicated **ST-LINK (SWD)** programming header.
  * Full breakout of unused GPIO pins to standard 2×40 SMD Male Pin Headers.

---

## 📐 PCB Layout & Design Considerations

The board was laid out on a **2-layer PCB** constrained within a compact **90 mm × 90 mm** form factor, adhering to standard fabrication capabilities:

1. **Decoupling & Signal Integrity:** Bypass capacitors (100 nF and bulk capacitors) are placed as close as possible to the MCU VDD pins. Signals are routed to pass through larger bulk capacitors first, followed by smaller high-frequency decoupling capacitors right at the IC pins.
2. **Power & Ground Planes:** Dual-layer copper polygon pours (Top and Bottom layers) are utilized for solid Ground (`GND`) distribution to minimize return path impedance and resolve isolated ground islands.
3. **High-Current Copper Zones:** 12V power nets are routed using wider copper pours/traces to safely handle current requirements with minimal voltage drop and thermal rise.
4. **Mechanical Mounting:** Includes 4 corner mounting holes for enclosure integration.

---

## 📋 Bill of Materials (Key Components)

| Component | Part Number / Value | Package | Qty | Description |
| :--- | :--- | :--- | :---: | :--- |
| **MCU** | `STM32F103RET6` | LQFP-64 | 1 | 32-bit ARM Cortex-M3 Microcontroller |
| **USB-UART IC** | `FT232RL` | SSOP-28 | 1 | USB to Serial UART Interface |
| **Voltage Regulator** | `LM78M05` | SMD (TO-252) | 1 | 5V Positive Voltage Regulator |
| **Transistor** | `BC817` | SOT-23 (SMD) | 3 | NPN Bipolar Transistor (Buzzer/LED Driver) |
| **Crystal (HSE)** | `8 MHz` | HC-49US | 1 | High-Speed External Oscillator |
| **Buzzer** | `AI-1223-TWT-5V-R` | SMD | 1 | 5V Magnetic Audio Transducer |
| **USB Connector** | `USB Type-C (C951)` | SMD | 1 | Power and Serial Data Connector |
| **Push Buttons** | `Tactile Switch` | SMD 3×6×2.5mm | 4 | Reset, Boot, and User Inputs |
| **LEDs** | `SMD LED` | 1210 | 5 | Power, TX/RX, and User I/O Indicators |
| **Capacitors** | `18pF, 100nF, 10µF, 47µF` | 1206 / 0805 | 13 | Oscillator Load, Filtering & Decoupling |
| **Resistors** | `10Ω, 4.7kΩ, 680Ω, 270Ω, 200kΩ`| 0805 | 20 | Current Limiting, Pull-up/Pull-down |
| **Pin Headers** | `2x40 Male Header` | SMD | 1 | GPIO Breakout & Expansion |

---

## 📁 Repository Structure

```text
├── Docs/
│   ├── Schematic.pdf          # Printable PDF of the hardware schematic
│   ├── PCB_2D_Layout.png      # 2D routing view of the PCB
│   └── PCB_3D_View.png        # 3D rendered view of the assembled board
├── pcb_micro.PrjPcb           # Altium Designer Project File
├── Sheet1.SchDoc              # Schematic Document
├── PCB1.PcbDoc                # PCB Layout Document
└── README.md                  # Project Documentation
