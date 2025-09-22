# Introduction to Verilog RTL design and Synthesis

## Introduction to open-source simulator iverilog

### <ins>**Simulator**</ins>
Simulator is a software tool used for simulating the design to verify the correctness.
iverilog is the tool used here. Simulator looks for the changes in the values of the input.
The output of the simulator remains same if there is no change in the input values.

### <ins>**Design**</ins>
Design is the actual verilog code that you want to implement in hardware.

### <ins>**TestBench**</ins>
Testbench is like a environment or setup that applies test vectors to the design to check if the outputs are correct  

<div align="center">
  <img width="500" height="250" alt="image" src="https://github.com/user-attachments/assets/8e3b10b0-b200-4537-88ea-540e064f83fb" />
</div>

### <ins>**How Simulator works**</ins>
### 

<div align="center">
  <img width="824" height="329" alt="image" src="https://github.com/user-attachments/assets/5ab70a47-df6b-448d-a163-16297bc3e9ae" />
</div>

### **Table of Contents**
  1. 
  2. 50 GB HDD
  3. Ubuntu 20.04+
  4. 4vCPU
  5. 
### **bsjkc**
# RTL design and Synthesis Using Sky130

This week is focussed on verilog RTL design, simulation, synthesis and optimization.


  - Various Flop coding styles and optimization
### <ins>**Yosys**</ins>
```bash

module good_mux (input i0 , input i1 , input sel , output reg y);
always @ (*)
begin
	if(sel)
		y <= i1;
	else 
		y <= i0;
end
endmodule


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
<div align="center">
  <img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/d471ae7a-2fab-47b1-9ccb-a5ac5bff32be" />
</div>

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
