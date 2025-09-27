# Combinational and Sequential Optimizations

## Introduction to Optimizations
In digital design **optimization** refers to the process of improving a design to meet specific objectives, such as performance, area, power or timing without changing its funcitonality. Optimization ensures the design works efficiently on hardware satisfying the constraints.

## Why optimization is important
- Reduce Area: Minimizes silicon usage and cost by reducing logic gates and registers.
- Improve Performance: Reduce critical path delay, allowing higher clock frequencies
- Save Power: Reduces switching activity, leaakage and dynamic power consumption
- Meet Timing Requirements: Ensures all signals arrive at flip-flops within the clock period 
- Enhance Manufacturability: Optimized designs are easier to route and more feasible.
  
## Differences between Combinational and Sequential optimizations
| Aspect | Combinational Optimization | Sequential optimization |
|--------|----------------------------|-------------------------|
|Elements Targetted| Logic gates (AND,OR etc)|Flip-flops, Latches and their interconnections|
|Main Goal| Reduce logic depth, area, delay|Improve timing, reduce registers, power savings|
  
## Combinational Logic Optimizations
- Squeezing the logic to get the most optimized design
    - Area and power savings
- Constant propogation
    - Direct optimization
- Boolean Logic optimization
    - K-map
    - Quine McKluskey

### <ins>**Constant Propogation**</ins>
<div align="center">
   <img width="940" height="454" alt="image" src="https://github.com/user-attachments/assets/7c311537-8285-46bc-919c-21d588a1c15f" />
</div>
In the above screenshot we can observe a NAND and OR gate. The output Y=(AB+C)'. If A=0, then the output=c'.When the above circuit is realized in the form of transistors, the no. of transistors get reduced from 6 to 2 thereby reducing the area and power.

### <ins>**Boolean Logic optimization**</ins>
<div align="center">
	<img width="940" height="422" alt="image" src="https://github.com/user-attachments/assets/0dbec27f-b924-46cb-93a6-0d448b0acf74" />
</div>

## Sequential Logic Optimizations
The techniques used are
- Basic
   - Sequential constant propagation
- Advanced (not covered as part of lab)
   - state optimization
   - Retiming
   - Sequntial Logic cloning (Floorplan aware synthesis)

An example of **sequential constant propagation** is shown below.
Consider a DFF with asynchronous reset with D as grounded. The output Q=0 when reset pin is there or when D is applied (since D is grounded Q=0). Q is connected to NAND gate where other input is A. The output of the NAND gate Y is always 1 irrespective of any value of A. If we consider a DFF with asynhronous set then Q=1 and when input D is applied Q=0. Which implies Q is dependent on set input and also on clock edge.
 
<div align="center">
	<img width="940" height="523" alt="image" src="https://github.com/user-attachments/assets/e7e0d754-46de-4c08-8393-efcd3d1e8746" />
</div>

An example of **Retiming** is shown below.
- Retiming is a sequential optimization technique where the flops are moved across combinational logic without changing the overall functionality of the circuit.The goal is to balance the path delays and improve performance.
- Retiming redistributes the registers to shorten the longest paths.
  
- Before retiming
    - path delay=5ns --> Max fequency=200MHZ
- After retiming
    - critical path reduced to 4ns ---> Max frequency=250MHZ

<div align="center">
	<img width="940" height="513" alt="image" src="https://github.com/user-attachments/assets/1e2f9798-ef3e-47e8-a59c-b6dc6b49687f" />
</div>

## Lab for Combinational Logic Optimizations
Command for optimization

<div align="center">
	
	<img width="940" height="513" alt="image" src="https://github.com/user-attachments/assets/1e2f9798-ef3e-47e8-a59c-b6dc6b49687f" />
</div>

### Optimizations for opt_check.v
<div align="center">
	<img width="903" height="91" alt="image" src="https://github.com/user-attachments/assets/47d91e2b-9ab8-420a-bc62-8f5ba5bc877e" />
	<img width="939" height="500" alt="image" src="https://github.com/user-attachments/assets/31bc73cd-f881-4af1-bcb3-c15dceb6d3dd" />
</div>

## Optimizations for opt_check2.v
<div align="center">
	<img width="900" height="91" alt="image" src="https://github.com/user-attachments/assets/98194100-c254-41ab-8fff-e887a84c4e41" />
	<img width="939" height="515" alt="image" src="https://github.com/user-attachments/assets/ad93fe26-3cc6-49b1-9db9-b56176f514e1" />
</div>

## Optimizations for opt_check3.v
<div align="center">
	<img width="836" height="102" alt="image" src="https://github.com/user-attachments/assets/8f2bb84d-44e9-4d19-be4d-b1c65e8587ea" />
	<img width="927" height="538" alt="image" src="https://github.com/user-attachments/assets/5ee4ec93-b72d-46bb-9106-9d4cb3e883d0" />
</div>

## Optimizations for opt_check4.v
<div align="center">
	<img width="867" height="89" alt="image" src="https://github.com/user-attachments/assets/004e1301-9a2c-4298-872f-9f9ea0e1e43f" />
	<img width="940" height="519" alt="image" src="https://github.com/user-attachments/assets/8a5e1caa-6203-4117-9820-cca452d83e4d" />
</div>


<div align="center">
    <img width="500" height="260" alt="image" src="https://github.com/user-attachments/assets/1f0d8586-5cb0-4a78-ba75-059aebde8979" />
</div>

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
