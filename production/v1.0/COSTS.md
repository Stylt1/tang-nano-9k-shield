# Cost estimate – rev 1.0

Rough price per board and for **5 boards** (JLCPCB minimum order). Prices in USD, without shipping, customs and VAT.

- **LCSC** – unit price from the LCSC tier shown (small-quantity tier).
- **est.** – estimate (part not checked on LCSC, or bought on AliExpress).
- Exact price: upload `gerbers.zip`, `bom.csv` and `cpl.csv` to JLCPCB – the quote shows the real total.

## SMD parts – assembled by JLCPCB

| Ref | Part | Qty/board | LCSC | Unit | Basis | Per board | 5 boards |
|---|---|---:|---|---:|---|---:|---:|
| U11 | RP2040 | 1 | C2040 | $1.10 | LCSC 1+ | $1.10 | $5.48 |
| U8 | W25Q32JVZPIQ flash 4 MB | 1 | C571260 | $1.38 | LCSC 1+ | $1.38 | $6.91 |
| U12 | TXS0108EPWR level shifter | 1 | C17206 | $0.41 | LCSC 1+ | $0.41 | $2.05 |
| U13 | TPS2065CDBVR USB load switch | 1 | C353882 | $0.26 | LCSC 5+ | $0.26 | $1.28 |
| U7 | TLV75518PDBV LDO 1.8 V | 1 | C2877863 | $0.21 | LCSC 5+ | $0.21 | $1.03 |
| U9 | USBLC6-2SC6 ESD | 1 | C7519 | $0.16 | LCSC 5+ | $0.16 | $0.82 |
| U3 | TLV75533PDBV LDO 3.3 V | 1 | C404027 | $0.12 | LCSC 5+ | $0.12 | $0.61 |
| U5 | TPS563201DDCR buck | 1 | C116592 | $0.07 | LCSC 10+ | $0.07 | $0.33 |
| J6 | USB-C GT-USB-7010ASV | 1 | C2988369 | $0.08 | LCSC 5+ | $0.08 | $0.42 |
| Q2–Q5 | BSS138 | 4 | C7420339 | $0.02 | LCSC 50+ | $0.08 | $0.39 |
| L1 | 3.3 µH SWPA6045S | 1 | C279943 | $0.15 | est. | $0.15 | $0.75 |
| Y1 | 12 MHz crystal 3225 | 1 | – | $0.10 | est. | $0.10 | $0.50 |
| D1–D3, D5, D6 | SS14 Schottky | 5 | C2480 | $0.02 | est. | $0.10 | $0.50 |
| 3V3, 5V | LED 0603 red / 0805 green | 2 | C2286, C2297 | $0.0077 | LCSC 100+ | $0.02 | $0.08 |
| C (15×) | 100 nF 0603 | 15 | C14663 | $0.02 | LCSC 50+ | $0.24 | $1.18 |
| C (5×) | 10 µF 1206 | 5 | C13585 | $0.03 | est. | $0.15 | $0.75 |
| C17, C19 | 22 µF 1206 | 2 | C12891 | $0.05 | est. | $0.10 | $0.50 |
| C (12×) | 1 µF / 100 nF / 15 pF 0603+0402 | 12 | C15849, C1525, C52923, C1644 | $0.0040 | est. | $0.05 | $0.24 |
| R (61×) | Resistors 0603, 14 values | 61 | C25804 … | $0.0024 | LCSC 100+ | $0.15 | $0.73 |
| | **Subtotal SMD parts** | | | | | **$4.91** | **$24.56** |

## Through-hole parts & module – hand-soldered (AliExpress estimates)

| Ref | Part | Qty/board | Unit | Per board | 5 boards |
|---|---|---:|---:|---:|---:|
| U2 | Tang Nano 9K module | 1 | $14.99 | $14.99 | $74.95 |
| U2 | 2× 1×24 female headers for Tang (not in BOM) | 1 | $0.30 | $0.30 | $1.50 |
| U1 | Dual stacked PS/2 (mini-DIN 6) | 1 | $1.00 | $1.00 | $5.00 |
| J2 | DE-15 HD VGA female, right angle | 1 | $0.80 | $0.80 | $4.00 |
| J1 | DC barrel jack | 1 | $0.30 | $0.30 | $1.50 |
| SW1, SW2 | DIP switch 8-pos | 2 | $0.25 | $0.50 | $2.50 |
| J8 | 2×6 right-angle female (Pmod) | 1 | $0.20 | $0.20 | $1.00 |
| J3, J5 | Pin headers 1×4, 1×7 | 1 | $0.08 | $0.08 | $0.40 |
| | **Subtotal through-hole** | | | **$18.17** | **$90.85** |

## PCB and assembly (5 boards)

| Item | Basis | Price |
|---|---|---:|
| 4-layer PCB 99.5 × 98.9 mm, 1.6 mm, JLC04161H-7628 | est. | $8.00 – $15.00 |
| Assembly setup fee (Economic PCBA) | JLCPCB | $8.18 |
| Stencil | JLCPCB | $1.53 |
| Extended parts fee, ~11 parts × $3.07 | JLCPCB, part count est. | $33.77 |
| SMD joints, 363 × 5 × $0.0016 | JLCPCB | $2.90 |
| **Subtotal PCB + assembly** | | **$54.38 – $61.38** |

## Total

| | 5 boards | Per board |
|---|---:|---:|
| With Tang Nano 9K modules | **$169.79 – $176.79** | $33.96 – $35.36 |
| Without Tang Nano 9K | $94.84 – $101.84 | $18.97 – $20.37 |

Notes:
- The extended-parts fee is charged per extended part type, so it hardly changes with the number of boards – per board it gets much cheaper with larger orders.
- Shipping from China to the EU and import VAT are not included.
