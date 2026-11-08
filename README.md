<div align="center">

# Tang Nano 9K Shield

**A retro‑computing & I/O expansion board for the Sipeed Tang Nano 9K FPGA**

VGA · dual PS/2 · RP2040 co‑processor · USB‑C · Pmod · 16 DIP switches · SPI / I²C headers

![KiCad](https://img.shields.io/badge/KiCad-10-314CB0?logo=kicad&logoColor=white)
![Layers](https://img.shields.io/badge/PCB-4%20layers-2E7D32)
![Size](https://img.shields.io/badge/size-100%20×%20100%20mm-555)
![FPGA](https://img.shields.io/badge/FPGA-Gowin%20GW1NR--9-orange)
![MCU](https://img.shields.io/badge/MCU-RP2040-C51A4A?logo=raspberrypi&logoColor=white)

<img width="3000" height="2000" alt="01_white_desk_flatlay" src="https://github.com/user-attachments/assets/8d082b64-95c1-4333-bd85-13104ec2b11a" />


</div>

---

## Table of contents

- [Overview](#overview)
- [Features](#features)
- [Gallery](#gallery)
- [Block diagram](#block-diagram)
- [Hardware](#hardware)
  - [Power](#power)
  - [Video – VGA](#video--vga)
  - [Input – PS/2](#input--ps2)
  - [RP2040 co‑processor](#rp2040-co-processor)
  - [Pmod](#pmod)
  - [Headers](#headers)
- [Pin mapping](#pin-mapping)
- [PCB](#pcb)
  - [Layer stack](#layer-stack)
- [Getting started](#getting-started)
- [Repository structure](#repository-structure)
- [Status](#status)
- [License](#license)

---

## Overview

The **Tang Nano 9K Shield** turns the tiny Sipeed Tang Nano 9K into a small,
self‑contained retro computer / FPGA playground. The FPGA drives a **VGA monitor**
and reads two **PS/2 devices** (keyboard + mouse). An on‑board **RP2040** acts as a
co‑processor: it talks to the FPGA over SPI, reads **16 DIP switches**, and exposes
**USB‑C**, **I²C** and **SPI** to the outside world. A level‑shifted **Pmod** port lets
you plug in standard Digilent‑compatible modules.

The board runs from a **7.5–15 V DC barrel jack**, from **USB‑C**, or from the
**Tang Nano’s own USB**, all OR‑ed together with Schottky diodes.

## Features

| | |
|---|---|
| 🖥️ **VGA output** | DE‑15 connector, 4‑bit‑per‑channel resistor DAC (4096 colours), HSYNC / VSYNC |
| ⌨️ **2 × PS/2** | Stacked mini‑DIN 6 (keyboard + mouse), 5 V ↔ 3.3 V bidirectional level shifting |
| 🧠 **RP2040 co‑processor** | 133 MHz dual Cortex‑M0+, 4 MB QSPI flash, 12 MHz crystal, BOOT / RESET jumpers |
| 🔌 **USB‑C** | RP2040 native USB with ESD protection, VBUS detection and a switchable 5 V output (USB host mode) |
| 🎛️ **16 DIP switches** | 2 × 8‑way slide switches with pull‑ups, read by the RP2040 |
| 🧩 **Pmod port** | 2 × 6 right‑angle socket, 8 lines translated 1.8 V ↔ 3.3 V (TXS0108E) |
| 📡 **Expansion** | 7‑pin SPI header (CS + INT) and 4‑pin I²C header (4.7 kΩ pull‑ups) |
| ⚡ **Flexible power** | 7.5–15 V DC jack → 5 V synchronous buck, USB‑C, or Tang USB; on‑board 3.3 V and 1.8 V LDOs |
| 💡 **Status LEDs** | 5 V and 3.3 V power indicators |

## Gallery

### Renders

| Top | Bottom |
|:---:|:---:|
| <img src="docs/images/render-top.jpg" alt="Top" width="100%"> | <img src="docs/images/render-bottom.jpg" alt="Bottom" width="100%"> |
| <img src="docs/images/render-angle.jpg" alt="Angled view" width="100%"> | <img src="docs/images/render-square.jpg" alt="Flat lay" width="100%"> |

### KiCad 3D views

| Top | Bottom |
|:---:|:---:|
| <img src="docs/images/kicad-top.jpg" alt="KiCad top" width="100%"> | <img src="docs/images/kicad-bottom.jpg" alt="KiCad bottom" width="100%"> |

| VGA side | PS/2 side |
|:---:|:---:|
| <img src="docs/images/kicad-vga.jpg" alt="VGA side" width="100%"> | <img src="docs/images/kicad-ps2.jpg" alt="PS/2 side" width="100%"> |

| DIP switches | Power & Pmod |
|:---:|:---:|
| <img src="docs/images/kicad-iso-dip.jpg" alt="DIP switches" width="100%"> | <img src="docs/images/kicad-iso-power.jpg" alt="Power and Pmod" width="100%"> |

### Copper layers

| F.Cu – top · GND pour · main signals | In1.Cu – inner 1 · GND reference plane |
|:---:|:---:|
| <img src="docs/images/layer-f-cu.png" alt="F.Cu layer" width="100%"> | <img src="docs/images/layer-in1-cu.png" alt="In1.Cu layer" width="100%"> |

| In2.Cu – inner 2 · 3V3 pour · power & tertiary signals | B.Cu – bottom · GND pour · secondary signals |
|:---:|:---:|
| <img src="docs/images/layer-in2-cu.png" alt="In2.Cu layer" width="100%"> | <img src="docs/images/layer-b-cu.png" alt="B.Cu layer" width="100%"> |

<sub>Renders: KiCad 3D raytracer composited onto CC0 surface textures from <a href="https://polyhaven.com">Poly Haven</a>.</sub>

## Block diagram

```text
                    ┌──────────────────────────────┐
  DC 7.5–15 V ──►   │  TPS563201 buck  →  5V_BUCK  │──┐
                    └──────────────────────────────┘  │
  USB‑C VBUS ─────────────────────────────────────────┼──► 5 V rail ──► TLV75533 ─► 3V3 ──► TLV75518 ─► 1V8
  Tang 5 V   ◄────────────────────────────────────────┘    (Schottky OR‑ing)

 ┌───────────────────────┐   SPI (CS1 / INT1)   ┌─────────────────────────┐
 │                       │◄────────────────────►│        RP2040           │
 │   Tang Nano 9K        │                      │  W25Q32 flash, 12 MHz   │
 │   (Gowin GW1NR‑9)     │                      │                         │
 │                       │── RGB 4:4:4 + sync ──► VGA (DE‑15)              ├──► USB‑C (ESD, VBUS switch)
 │                       │◄─ 2 × CLK/DATA ──────► BSS138 ──► PS/2 × 2       ├──► 16 × DIP switch
 │                       │◄─ 8 lines @1.8 V ────► TXS0108E ──► Pmod (3.3 V)├──► I²C header
 │                       │◄─ SPI (CS2 / INT2) ──► SPI header               │
 └───────────────────────┘                      └─────────────────────────┘
```

## Hardware

### Power

| Rail | Source | Part | Notes |
|---|---|---|---|
| **VIN** | DC barrel jack, **7.5–15 V, centre positive** | SS14 | Reverse‑polarity protection |
| **5V_BUCK** | VIN | TPS563201 | Synchronous buck, set to 5.07 V (56 k / 10 k divider) |
| **5V** | 5V_BUCK / USB‑C / Tang 5 V | 4 × SS14 | Diode OR‑ing of all three sources |
| **3V3** | 5V | TLV75533 | RP2040, logic, pull‑ups, Pmod VCC |
| **1V8** | 3V3 | TLV75518 | Side A of the Pmod level shifter (FPGA bank 3) |

> [!NOTE]
> The Tang Nano’s own 3.3 V pin is intentionally **not** used. The shield generates its own 3.3 V.

### Video – VGA

- 12 FPGA outputs → 4‑bit binary‑weighted resistor DAC per channel
  (**510 Ω / 1 kΩ / 2 kΩ / 3.9 kΩ**) → ~0.7 V full scale into the monitor’s 75 Ω.
- HSYNC / VSYNC through 100 Ω series resistors.
- 4096 colours (RGB 4:4:4).

### Input – PS/2

- Stacked dual mini‑DIN 6: **top = mouse (purple)**, **bottom = keyboard (green)**.
- Bidirectional open‑drain level shifting with **BSS138** MOSFETs (5 V ↔ 3.3 V),
  4.7 kΩ pull‑ups on both sides, 330 Ω series resistors on the connector side.

### RP2040 co‑processor

- RP2040 + **W25Q32JV** 4 MB QSPI flash + **12 MHz** crystal (Raspberry Pi reference design).
- **BOOT** and **RESET** solder jumpers for entering the USB bootloader.
- **USB‑C**: USBLC6‑2SC6 ESD protection, 27 Ω series resistors, 5.1 kΩ CC pull‑downs.
- **USB host power**: TPS2065C load switch can supply 5 V on VBUS (enable + fault signals on GPIO).
- **VBUS detect** through a 15 k / 20 k divider.

### Pmod

- Standard **Digilent Pmod™ 2 × 6** host socket (right‑angle, female).
- 8 signal lines driven from FPGA **bank 3 (1.8 V)** and translated to **3.3 V** by a **TXS0108E**.
- Pin 1 marked on the silkscreen, pinout table printed on the back of the board.

### Headers

| Header | Pins |
|---|---|
| **SPI** (J5) | GND · 3V3 · SCK · MOSI · MISO · CS · INT |
| **I²C** (J3) | GND · 3V3 · SDA · SCL |

## Pin mapping

<details>
<summary><b>FPGA (Tang Nano 9K) pins</b></summary>

| Function | FPGA pin(s) | I/O standard |
|---|---|---|
| VGA R0 · R1 · R2 · R3 | 57 · 56 · 55 · 54 | 3.3 V |
| VGA G0 · G1 · G2 · G3 | 53 · 51 · 42 · 41 | 3.3 V |
| VGA B0 · B1 · B2 · B3 | 35 · 40 · 34 · 33 | 3.3 V |
| VGA HSYNC · VSYNC | 30 · 29 | 3.3 V |
| PS/2 #1 CLK · DATA | 49 · 48 | 3.3 V |
| PS/2 #2 CLK · DATA | 32 · 31 | 3.3 V |
| SPI SCK · MOSI · MISO | 36 · 37 · 39 | 3.3 V |
| SPI CS1 · INT1 (RP2040) | 25 · 26 | 3.3 V |
| SPI CS2 · INT2 (header) | 27 · 28 | 3.3 V |
| Pmod 1 · 2 · 3 · 4 | 86 · 84 · 82 · 80 | **1.8 V** |
| Pmod 7 · 8 · 9 · 10 | 85 · 83 · 81 · 79 | **1.8 V** |

</details>

<details>
<summary><b>RP2040 GPIOs</b></summary>

| GPIO | Function |
|---|---|
| GPIO0 – GPIO15 | DIP switches SW1 – SW16 (active low, 10 kΩ pull‑up) |
| GPIO16 | SPI0 RX ← MOSI |
| GPIO17 | SPI0 CS ← CS1 |
| GPIO18 | SPI0 SCK |
| GPIO19 | SPI0 TX → MISO |
| GPIO20 | INT1 → FPGA |
| GPIO21 | USB_PWR_EN (TPS2065C enable) |
| GPIO22 | I²C1 SDA |
| GPIO23 | I²C1 SCL |
| GPIO24 | VBUS_DET |
| GPIO25 | USB_FLT (over‑current flag, active low) |
| GPIO26 – GPIO29 | free (ADC0 – ADC3) |

</details>

<details>
<summary><b>Pmod port (J8)</b></summary>

| Pmod pin | Signal | | Pmod pin | Signal |
|:---:|:---:|---|:---:|:---:|
| 1 | PMOD1 | | 7 | PMOD7 |
| 2 | PMOD2 | | 8 | PMOD8 |
| 3 | PMOD3 | | 9 | PMOD9 |
| 4 | PMOD4 | | 10 | PMOD10 |
| 5 | GND | | 11 | GND |
| 6 | 3V3 | | 12 | 3V3 |

</details>

## PCB

| | |
|---|---|
| **Size** | ~100 × 100 mm |
| **Layers** | 4 – F.Cu / In1.Cu / In2.Cu / B.Cu (see [Layer stack](#layer-stack)) |
| **Stackup** | JLCPCB JLC04161H‑7628, 1.6 mm, 1 oz outer / 0.5 oz inner |
| **Min. via** | 0.45 / 0.2 mm |
| **Components** | SMD 0603 / 0402 passives, SOT‑23, QFN‑56, TSSOP‑20 + THT connectors |
| **EDA** | KiCad 10 |

### Layer stack

| # | Layer | Copper pour (fill) | Routed on this layer |
|:---:|---|---|---|
| 1 | **F.Cu** (top) | GND | Main signals, component fan‑out |
| 2 | **In1.Cu** (inner 1) | GND – solid plane | Reference ground for the top‑layer signals |
| 3 | **In2.Cu** (inner 2) | 3V3 | Power distribution, tertiary signals |
| 4 | **B.Cu** (bottom) | GND | Secondary signals |

Images of each copper layer are in the [Gallery](#copper-layers).

Custom 3D models for the Tang Nano 9K, PS/2, VGA, DIP switches and DC jack are included in [`3dmodels/`](3dmodels).

## Getting started

### Ordering
1. Open `tang-nano-9k-shield.kicad_pcb` in KiCad 10.
2. Export Gerbers + drill files (**File → Fabrication Outputs**).
3. Order as a **4‑layer** board using the **JLC04161H‑7628** stackup.
4. The schematic contains **LCSC** part numbers for assembly.

### Bring‑up
1. Power the board from a **current‑limited** supply on the DC jack, *without* the Tang Nano, and check **5 V, 3.3 V and 1.8 V**.
2. Connect USB‑C while bridging **BOOT**. The RP2040 should enumerate as **RPI‑RP2**.
3. Flash the RP2040 firmware, then plug in the Tang Nano 9K.
4. Load an FPGA bitstream (e.g. a VGA test pattern) using the pin mapping above.

> [!WARNING]
> Pmod lines are driven from the FPGA’s **1.8 V bank**. Set those pins to `LVCMOS18` in your constraints file.

## Repository structure

```text
tang-nano-9k-shield/
├── tang-nano-9k-shield.kicad_pro   # KiCad project
├── tang-nano-9k-shield.kicad_sch   # Schematic
├── tang-nano-9k-shield.kicad_pcb   # PCB layout
├── block_diagram.kicad_sch         # Block diagram
├── 3dmodels/                       # Custom 3D models (VRML / STEP)
├── datasheets/                     # Component datasheets + INDEX.md
└── docs/images/                    # Renders and copper-layer images used in this README
```

## Status

- [x] Schematic
- [x] PCB layout & routing (DRC: 0 unconnected)
- [x] 3D models & renders
- [ ] Prototype manufactured
- [ ] Hardware bring‑up
- [ ] RP2040 firmware
- [ ] FPGA example designs (VGA, PS/2, SPI bridge)

## License

<!-- Choose a license, e.g. CERN‑OHL‑S‑2.0 for hardware and MIT for firmware -->
© 2026 Stylt. License to be added.

---

<div align="center">
Made with ❤️ and KiCad
</div>
