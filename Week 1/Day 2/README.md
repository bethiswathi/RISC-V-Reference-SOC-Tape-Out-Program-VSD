# Timing libs, Hierachical vs Flat synthesis and Efficient Flop Coding Styles

## Introduction to Timing .libs
Libraries are characterized based on PVT conditions
Process --> Variations due to fabrication
Voltage --> Variations due to voltage
Temperature --> Variations due to temperature

Below is the screenshot of the .lib file
tt stands for typical in the .lib name
025 stands for temperature of 25 C in the .lib name
1v80 stands for 1.8v in the .lib name

<div align="center">
  <img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/0f7135e9-549e-46e3-a742-fc097229d84c" />
</div>

.lib contains the following information related to each cell.
- Area
- Power
- Leakage power based on combination of inputs
- Power associated with the pin
- Transition
- Delay
- Input capacitance


### <ins>**Hierachical Synthesis**</ins>
Hierachical Synthesis preserves module boundaries, enabling easier debugging, reuse and modular optimization but may miss some global optimizations. 
Flat Synthesis removes hierachy, allowing global optimizations and potentially better performance/area but increases complexity and runtime. 
 
<div align="center">
  <img width="700" height="300" alt="image" src="https://github.com/user-attachments/assets/805a56d3-6786-454a-b025-4ba84b907e34" />
  <img width="400" height="300" alt="image" src="https://github.com/user-attachments/assets/8a92a66f-ccf2-4a83-af2b-adfd11586328" />
</div>
Above is the example of Hierachical synthesis of multiple_modules.v. The following is the report after synthesizing multiple_modules.v. From the screen shot we can observe that module1 has 1 AND gate whereas module2 has 1 OR gate. 

Hierachy is preserved here. We see the sub-modules instead of the AND ,OR gates when we run show command.
<div align="center">
  <img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/bfb6d014-158e-44ee-afcc-f50a147e6ab5" />
  <img width="600" height="300" alt="image" src="https://github.com/user-attachments/assets/c2405a31-2332-4135-8dcc-167b473cc070" />
</div>

### <ins>**Flat Synthesis**</ins> 
Flat Synthesis removes hierachy, allowing global optimizations and potentially better performance/area but increases complexity and runtime. 
<div align="center">
  <img width="600" height="300" alt="image" src="https://github.com/user-attachments/assets/25d3e970-6d9a-47f9-8527-3de4af01f92f" />
</div>
command to write flat netlist

- flatten 

## Sub Module Lvel Synthesis
Sub module level synthesis optimizes each module individually balancing performance, area and power within its scope.
It enables modular design reuse and faster compilation but may miss some cross modular global optimizations.

<div align="center">
  <img width="500" height="250" alt="image" src="https://github.com/user-attachments/assets/5ab70a47-df6b-448d-a163-16297bc3e9ae" />
</div>
Iverilog is a open-source verilog simulation tool.The design (HDL code) and testbench are compiled and simulated using iverilog. The simulation generates VCD (Value Change Dump) file which records all the signal changes over simkulation time. The VCD file is loaded into GTKWave, a tool to visulaize signal waveforms.


## Various Flop Coding Styles and Optimization

  





## Introduction to Yosys and Logic Synthesis
<div align="center">
    <img width="500" height="260" alt="image" src="https://github.com/user-attachments/assets/1f0d8586-5cb0-4a78-ba75-059aebde8979" />
</div>
Yosys is a powerful open-source logic synthesis tool used in digital VLSI design. The design is given to yosys tool using read_verilog and the library files using read_liberty. Yosys tool synthesizes the design using the library cells and the output is a netlist file (gate-level representation of the design). Netlist should be same as the design but represented in the form of standard cells.

## Why do libraries have Different Flavours of Gates?
A .lib contains multiple flavours of the same gate. Flavours differ by drive strength (X1,X2,X4), threshold voltage (LVT,SVT,HVT). This allows power-performance-area trade-offs during the design. Critical paths use faster gates while non-critical paths use slower,low-power gates.

## Introduction To Logic Synthesis
<div align="center">
   <img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/3eabe123-17df-47e6-be98-11eafed373fe" />
</div>

## Lab Using Yosys and Sky130 PDK


#### <ins>**Iverilog**</ins>
```bash
$ sudo apt-get 
$ sudo apt-get install iverilog
```
<img width="500" height="507" alt="image" src="https://github.com/user-attachments/assets/f168cc2f-e880-4a99-8838-d3a68cd9760a" />

#### <ins>**gtkwave**</ins>
```bash
$ sudo apt-get update
$ sudo apt install gtkwave
```
<img width="500" height="120" alt="image" src="https://github.com/user-attachments/assets/6b95cca0-fdb1-4407-b8f6-1b6ad72bb8ce" />

