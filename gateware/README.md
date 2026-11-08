# Gateware – Tang Nano 9K (Gowin GW1NR-9)

FPGA designs for the shield.

Layout:

```text
gateware/
├── constraints/
│   └── tang-nano-9k-shield.cst   # pin constraints for all shield I/O
└── examples/                     # planned: VGA test pattern, PS/2, SPI bridge
```

Pin mapping: see the FPGA table in the main [README](../README.md#pin-mapping).
Pmod lines are on bank 3 (1.8 V) – use `LVCMOS18` for them.

Gowin IDE output (`impl/`) is ignored by git.
