# STM32F103RET6 Evaluation Board — Hardware & PCB Design

A custom two-layer printed circuit board (PCB) and hardware schematic for an STM32F103RET6 ARM Cortex-M3 microcontroller evaluation board, designed using Altium Designer.

The project covers component selection based on datasheets, schematic capture, PCB layout, component placement, routing, and copper polygon configuration.

## Project Status

- **Schematic design:** Completed
- **PCB layout:** Completed
- **Physical fabrication:** Not performed
- **Hardware testing:** Not performed

This repository documents the electronic design work completed as part of an undergraduate engineering course. The physical board has not been fabricated or experimentally validated.

## Key Hardware Features

- **Microcontroller:** STM32F103RET6 (ARM Cortex-M3, LQFP-64)
- **Clock System:**
  - HSE: External 8 MHz crystal with 18 pF load capacitors
  - LSE: 32.768 kHz crystal for the real-time clock (RTC)
- **Power Supply:**
  - 12 V DC input regulated to 5 V using an LM78M05 linear regulator
  - USB Type-C 5 V bus-power input option
- **USB-to-UART Interface:** FT232RL USB-to-serial converter
- **User I/O:**
  - Three user push buttons
  - Reset and boot-mode selection circuits
  - Transistor-driven LED and buzzer circuits
- **Programming and Expansion:**
  - Dedicated ST-LINK/SWD programming header
  - GPIO breakout through 2×40 pin headers

## PCB Layout and Design Considerations

The PCB was designed as a two-layer board with a target form factor of 90 × 90 mm.

The documented design considerations include:

1. **Decoupling capacitors:** Placement of bypass capacitors near the microcontroller power pins.
2. **Power and ground distribution:** Copper polygon pours on the top and bottom layers for power and ground connections.
3. **Power routing:** Consideration of trace widths for power nets.
4. **Component placement and routing:** Placement of components and routing of signal connections while addressing schematic and PCB connectivity issues.
5. **Mechanical design:** Four corner mounting holes for potential enclosure integration.

These are design considerations; electrical performance and manufacturing readiness have not been experimentally verified.

## Bill of Materials

The design includes the following major components:

| Component | Part Number / Value | Purpose |
|---|---|---|
| Microcontroller | STM32F103RET6 | Main processing unit |
| USB-to-UART IC | FT232RL | USB-to-serial communication |
| Voltage Regulator | LM78M05 | 5 V regulation |
| Transistor | BC817 | LED and buzzer switching |
| HSE Crystal | 8 MHz | High-speed clock source |
| LSE Crystal | 32.768 kHz | RTC clock source |
| USB Connector | USB Type-C | USB interface and power input |
| Buzzer | AI-1223-TWT-5V-R | Audio output |
| Push Buttons | SMD tactile switches | User input, reset, and boot control |
| LEDs | SMD 1210 | Status and user indication |
| Pin Headers | 2×40 | GPIO expansion |

For the complete component list, refer to [`bill of material.csv`](bill%20of%20material.csv).

## Repository Contents

```text
STM32F103-Evaluation-Board-PCB/
├── Images/
├── pcb_micro.PrjPcb
├── Sheet1.SchDoc
├── PCB1.PcbDoc
├── bill of material.csv
└── README.md
```

- **`pcb_micro.PrjPcb`** — Altium Designer project file
- **`Sheet1.SchDoc`** — Schematic document
- **`PCB1.PcbDoc`** — PCB layout document
- **`bill of material.csv`** — Bill of materials
- **`Images/`** — Project images, if available

## Tools

- Altium Designer
- Electronic schematic design
- PCB layout and routing
- Datasheet-based component selection

## Author

**Parsa Ghorbani**

Electrical Engineering | Control Engineering
