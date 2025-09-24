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

## Iverilog based simulation flow
<div align="center">
  <img width="500" height="250" alt="image" src="https://github.com/user-attachments/assets/5ab70a47-df6b-448d-a163-16297bc3e9ae" />
</div>
Iverilog is a open-source verilog simulation tool.The design (HDL code) and testbench are compiled and simulated using iverilog. The simulation generates VCD (Value Change Dump) file which records all the signal changes over simkulation time. The VCD file is loaded into GTKWave, a tool to visulaize signal waveforms.

## Lab Using iverilog and gtkwave
<div align="center">
    <img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/73e8f45c-d1d6-4275-b51d-0e15714e2c48" />
</div>
The output of iverilog is a .vcd file and a.out is created. By executed a.out iverilog dumps the vcd file.
gtkwave is used to generate the waveform and display in visual format.
The waveform is shown as below
<div align="center">
    <img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/beef54e0-63c0-4f5f-837b-5213a8053574" />
</div>



## Verilog Code Analysis

module good_mux (input i0 , input i1 , input sel , output reg y);
always @ (*)
begin
	if(sel)
		y <= i1;
	else 
		y <= i0;
end
endmodule

## Introduction to Yosys and Synthesis
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
<div align="center">
	<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/fd1b03d3-0ec2-45dd-a3fb-9497318eba34" />
	<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/185e1998-e528-467e-a758-d96a0dc3f91b" />
    <img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/071abaf4-5993-495f-ba3c-40fb542f70d4" />
    <img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/a5825841-cf0d-48ac-a17d-89abe9b304ce" />
	<img width="651" height="376" alt="image" src="https://github.com/user-attachments/assets/ea8df5cf-5446-48e3-8427-26fdfb444eec" />
</div>

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
