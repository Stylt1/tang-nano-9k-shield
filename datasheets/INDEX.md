# Datasheety – index

Vyplní sa pri overení (skill `pcb-component-research`). Strany zapisuj až po prečítaní dokumentu.

| Ref | Súčiastka | Výrobca | Súbor | Revízia | Pinout | Abs. max | Odporúčané zapojenie | Layout |
|-----|-----------|---------|-------|---------|--------|----------|----------------------|--------|
| U2  | Tang Nano 9K (GW1NR-9) | Sipeed / Gowin | Tang_Nano_9K_3674_schematic.pdf | 3674 (2024-03-11) | s.2 (header J5/J6) | | | |
| U11 | RP2040 | Raspberry Pi | RP2040_datasheet.pdf, Hardware_design_with_RP2040.pdf | build-date 2025-02-20 | s.238–239 (Table 279 GPIO funkcie) | | | |
| U8  | W25Q32JVZP (WSON 6x5) | Winbond | W25Q32JV_winbond.pdf | Revision G | s.6 (3.3 Pin Description: 1 /CS, 2 DO, 3 /WP, 4 GND, 5 DI, 6 CLK, 7 /HOLD, 8 VCC) | s.5 (VCC 2,7–3,6 V) | | s.70 (EP: nezapojený alebo GND, bez via pod padom) |
| Y1  | X322512MSB4SI (rad YSX321SL) | YXC | YXC_YSX321SL_X322512MSB4SI.pdf (z JLCPCB) | – | s.1 (kryštál #1–#3, GND #2/#4) | | ESR 12–15 MHz max 80 Ω, C0 3 pF, DL 10–200 µW, CL 10/20 pF podľa objednávky (20 pF pre tento PN len podľa LCSC) | s.1 (land pattern) |
| (Y1 náhrada) | ABM8-272-T3 | Abracon | ABM8-272-T3.pdf | Drawing 456603 rev. B (2024-09-16) | s.4 (top view: kryštál 1–3, GND 2/4) | | s.2 (12 MHz, CL 10 pF, ESR max 50 Ω, C0 3 pF, DL 10–200 µW) | |
| U9  | USBLC6-2SC6 | ST | (st.com blokuje curl/WebFetch – stiahnuť ručne) | | | | | |
| U5  | TPS563201DDCR | TI | tps563201.pdf | SLVSD90B (2024-09) | s.3 (Table 4-1) | s.4 (ROC: VIN 4,5–17 V, EN ≤17 V) | s.14 (VOUT = 0,768·(1+R1/R2)), s.15 (Table 7-2: 5 V → R1 54,9k, R2 10k, L 3,3 µH, COUT 20–68 µF; CIN >10 µF keramika, napäťovo > VIN max), s.16 (VBST 0,1 µF) | |
| U3 (pôvodne) | AMS1117-3.3 – nahradené TLV75533 | AMS | AMS1117.pdf | (bez revízie) | s.1 (SOT-223: 1 GND, 2 VOUT, 3 VIN) | s.2 (VIN max 15 V) | s.3 (dropout 1,1/1,3 V @0,8 A; min. záťaž 10 mA, Note 5), s.4 (stabilita: 22 µF tantal na výstupe) | |
| U7 (pôvodne) | AMS1117-1.8 – nahradené TLV75518 | AMS | AMS1117.pdf | – | ako U3 | | ako U3 | |
| U4  | PT8211 | Princeton | | | | | | |
| U6  | TPA6132A2RTE | TI | | | | | | |
| U10 | MAX3232 | TI / ADI | | | | | | |
| Q1  | SS8050 | | | | | | | |
| D1-3| SS14 | Vishay | SS14_vishay.pdf | 88746 (2020-04-23) | | s.1 (IF(AV) 1 A) | s.2 (VF max 0,50 V @1 A) | |
| D4  | 1N4148W | | | | | | | |
| U12 | TXS0108EPW (TSSOP-20) | TI | TXS0108E.pdf | SCES642L (rev. 2024-11) | s.4 (Table 4-1) | | s.1, s.19–20 (8.2, 8.3: OE pull-down pre Hi-Z pri nábehu; VCCA ≤ VCCB; 0,1 µF na VCCA/VCCB); s.18 (7.3.5 interné pull-upy 4k/40k) | s.20 (8.4.1) |
| J8  | Pmod 2×6 | Digilent | (Pmod Interface Spec – stiahnuť ručne, digilent.com blokuje automatický prístup) | | | | | |
| Q2–Q5 | BSS138 (SOT-23) | onsemi | BSS138_onsemi.pdf | Rev. 7 (2024-04) | s.1 (marking diagram: 1=G, 2=S, 3=D) | s.2 (VDSS 50 V, VGS ±20 V) | s.2 (VGS(th) 0,8–1,5 V) | |
| J6  | GT-USB-7010ASV (USB-C 16P) | G-Switch | GT-USB-7010ASV_C2988369.pdf (výkres z JLCPCB, len obrázok) | A0 (2023-02-04) | s.1 (tabuľka A1–A12/B1–B12) | 3 A VBUS, 24 V AC | | s.1 (Recommended PCB layout) |
| U3, U7 | TLV75533PDBV, TLV75518PDBV (SOT-23-5) | TI | tlv755p.pdf | SBVS320D (2024-09) | s.3 (DBV: 1 IN, 2 GND, 3 EN, 4 NC, 5 OUT) | s.4 (VIN/EN max 6 V; ROC IOUT 0–500 mA, CIN/COUT ≥1 µF, COUT ≤200 µF) | s.6 (dropout 3,3 V: max 215 mV @500 mA; 1,8 V: max 380 mV), s.15 (MLCC derating 50 %) | s.5 (RθJA DBV 231 °C/W JEDEC, 100,8 EVM) |
| U13 | TPS2065CDBVR (SOT-23-5) | TI | TPS20xxC_tps2051c.pdf | SLVSAU6I (2026-05) | s.3–4 (DBV: 1 OUT, 2 GND, 3 FLT, 4 EN, 5 IN), s.3 (tabuľka variantov) | s.5 (VIN 4,5–5,5 V, EN VIH ≥ 2 V) | s.7 (IOS 1A typ: 1,3/1,55/1,8 A), s.8 (IREV max 20 µA), s.4/s.18 (CIN ≥ 0,1 µF + 1–22 µF; COUT 120 µF pre USB, inak ≥ 10 µF) | s.22 |
| (Tang U23) | TMI7003C (PMU na doske Tang Nano 9K) | TOLL / TMI | TMI7003C_Tang-PMU.pdf | V1.5 (2024-07) | | s.4 (ROC VIN 2,5–5,5 V) | s.1 (100 % duty v dropoute), s.5 (UVLO 2,3 V, OVP 6,0 V, PMOS 300 mΩ, Ipeak 1,5 A) | |
| D8 | KT-0603R červená LED 0603 (LCSC C2286, JLC Basic) | Hubei KENTO | KT-0603R_C2286.pdf | A.0 (2018-12-06) | s.2 (rozmery, pady) | s.3 (IF 25 mA DC, Pd 40 mW, VR 5 V) | s.3 (VF 1,8–2,4 V @20 mA; IV 145–300 mcd @20 mA) | s.2 |
| D7 | KT-0805G zelená LED 0805 (LCSC C2297, JLC Basic) | Hubei KENTO | KT-0805G_C2297.pdf | A.0 (2018-12-06) | s.2 (rozmery, pady) | s.3 (IF 30 mA DC, Pd 100 mW, VR 5 V) | s.3 (VF 2,6–3,1 V @5 mA; IV 175–430 mcd @5 mA) | s.2 |
