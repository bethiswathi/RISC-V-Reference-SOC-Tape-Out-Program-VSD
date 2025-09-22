# Introduction to Verilog RTL design and Synthesis

## Introduction to open-source simulator iverilog

### **Oracle Virtual machine link**
https://www.virtualbox.org/wiki/Downloads
<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/7bd19570-d25a-4dfb-92fc-91abad89e48b" />

### **Table of Contents**
<details>
  <summary> Day 1- Introduction to verilog RTL design and Synthesis</summary>

  - Introduction to open-source simulator iverilog
  - Labs using iverilog and gtkwave
  - Introduction to Yosys and Logic synthesis
  - Labs using Yosys and Sky 130 PDKs

</details>
<details>
  <summary> Day 2- Timing libs, hierachical vs flat synthesis and efficient flop coding styles</summary>

  - Introduction to timing .libs
  - Hierachical vs Flat synthesis
  - Various Flop coding styles and optimization
    
</details>
<details>
  <summary> Day 3- Combinational and sequential optimizations</summary>

  - Introduction to optimizations
  - Combinational logic optimizations
  - Sequential logic optimizations
  - Sequential optimizations for unused outputs
  
</details>
<details>
  <summary> Day 4- GLS,blocking vs non-blocking and Synthesis-Simulation mismatch</summary>

  - GLS, Synthesis-simulation mismatch and blocking/Non-blocking statements
  - Labs on GLS and synthesis-simulation Mismatch
  - Labs on synth-sim mismatch for blocking statement

</details>
<details>
  <summary> Day 5- Optimization in synthesis</summary>
  
  - If case constructs
  - Labs on "Incomplete if Case"
  - Labs on "Incomplete overlapping Case"
  - for loop and for generate
  - Labs on "for loop" and "for generate"
  
</details>
  
### **Tool Check**

### <ins>**Yosys**</ins>
```bash
$ sudo apt-get update
$ git clone http://github.com/YosysHQ/yosys
$ cd yosys
$ sudo apt install make
$ sudo apt-get install build-essential clangbison flex \
  libreadline-dev gawk tcl-dev libffi-devgit \
  graphviz xdotpkg-config python3 libboost -system-dev \
  libboost -python-dev libboost-filesystem-dev zlib1g-dev
$ make config-gcc
$ git submodule update --init --recursive
$ make
$ sudo make install
```
<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/d471ae7a-2fab-47b1-9ccb-a5ac5bff32be" />

#### <ins>**Iverilog**</ins>
```bash
$ sudo apt-get update
$ sudo apt-get install iverilog
```
<img width="500" height="507" alt="image" src="https://github.com/user-attachments/assets/f168cc2f-e880-4a99-8838-d3a68cd9760a" />

#### <ins>**gtkwave**</ins>
```bash
$ sudo apt-get update
$ sudo apt install gtkwave
```
<img width="500" height="120" alt="image" src="https://github.com/user-attachments/assets/6b95cca0-fdb1-4407-b8f6-1b6ad72bb8ce" />

