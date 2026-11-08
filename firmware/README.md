# Firmware – RP2040

Firmware for the on-board RP2040 co-processor (not written yet).

Planned functions, per the shield's pin plan (see the RP2040 GPIO table in the main [README](../README.md#pin-mapping)):

- read the 16 DIP switches
- SPI slave link to the FPGA (CS1 / INT1)
- USB-C device / host (VBUS switch, over-current flag)
- I²C header

Build output (`build/`) is ignored by git.
