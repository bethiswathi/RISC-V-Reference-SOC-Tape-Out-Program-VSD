# BabySoC Fundamentals and Functional Modelling

## Problem Statement
This work discusses the different aspects of designing a small, compact and open-source **System-on-Chip** (SoC) based on **RVMYTH** a 
RISC-V based processor. This SoC integrates a **Phase Locked Loop (PLL)** for clock generation and control and a **10-bit Digital-to-Analog-Converter (DAC)** for communicating with outside world. By converting digital signals into analog, this DAC allows BabySoC to communicate with the devices such as television and mobile phones which accepts the analog inputs and whose output is in the form of audio or video.  
built with **Sky130 technology**, it serves as a **well-documented educational platform** for learning and experimenting with digital-analog interfacing.  

### <ins>**Simulator**</ins>
Simulator is a software tool used for simulating the design to verify the correctness.
iverilog is the tool used here. Simulator looks for the changes in the values of the input.
The output of the simulator remains same if there is no change in the input values.

### <ins>**Design**</ins>
Design is the actual verilog code that you want to implement in hardware.

### <ins>**TestBench**</ins>
Testbench is like a environment or setup that applies test vectors to the design to check if the outputs are correct  

