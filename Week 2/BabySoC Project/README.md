# Overview
**VSDBabySoC** is a simple SoC integrating the RISC-V processor (rvmyth), a PLL and a DAC. This project focusses on IP core integration and validating the design through pre-synthesis and post-synthesis simulations.

## Project Structure
- src/include/  - Contains header files (*.vh) with macros/parameters
- src/module/   - Contains verilog source files for SoC modules
- output/       - stores compiled outputs and simulated results

## Tools Required
- **Icarus Verilog** for compilation
- **Gtkwave** for viewing waveforms


## Module Descriptions
### **1. vsdbabysoc.v (Top-Level SoC Module)**
This is the top-level module that integrates the rvmyth, PLL and DAC modules.
