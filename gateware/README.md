# Gateware – Tang Nano 9K (Gowin GW1NR-9)

```text
gateware/
└── constraints/
    └── tang-nano-9k-shield.cst   # pin constraints for all shield I/O
```

Add `constraints/tang-nano-9k-shield.cst` to your Gowin project and name the
top-level ports as in the file (`vga_r[3:0]`, `ps2_clk[1:0]`, `pmod[7:0]`, …).
Comment out constraints for ports your design does not use.

- Bank voltages: VGA, PS/2, SPI, clock = `LVCMOS33`; Pmod, LEDs, buttons = `LVCMOS18`.
- PS/2 lines are open-drain: drive `0` or `z`, external 4.7k pull-ups are on the shield.
- The SPI bus is shared with the Tang's microSD slot – keep `sd_cs` (pin 38) HIGH when not using it.
- Pin 4 (`btn[1]`) is JTAG_SEL: enable *Dual-Purpose Pin → Use JTAG as regular IO* to use it.

Pin mapping overview: see the main [README](../README.md#pin-mapping).
