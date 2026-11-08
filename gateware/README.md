# Gateware – Tang Nano 9K (Gowin GW1NR-9)

FPGA designs for the shield (not added yet).

Planned layout:

```text
gateware/
├── constraints/      # shared .cst pin constraints for the shield
└── examples/         # e.g. VGA test pattern, PS/2 keyboard, SPI bridge
```

Pin mapping: see the FPGA table in the main [README](../README.md#pin-mapping).
Pmod lines are on bank 3 (1.8 V) – use `LVCMOS18` for them.

Gowin IDE output (`impl/`) is ignored by git.
