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
	<img width="740" height="500" alt="image" src="https://github.com/user-attachments/assets/e7e0d754-46de-4c08-8393-efcd3d1e8746" />
</div>

An example of **Retiming** is shown below.
- Retiming is a sequential optimization technique where the flops are moved across combinational logic without changing the overall functionality of the circuit.The goal is to balance the path delays and improve performance.
- Retiming redistributes the registers to shorten the longest paths.
  
- Before retiming
    - path delay=5ns --> Max fequency=200MHZ
- After retiming
    - critical path reduced to 4ns ---> Max frequency=250MHZ

<div align="center">
	<img width="740" height="500" alt="image" src="https://github.com/user-attachments/assets/1e2f9798-ef3e-47e8-a59c-b6dc6b49687f" />
</div>

## Lab for Combinational Logic Optimizations
Command for optimization
<div align="left">
	<img width="200" height="40" alt="image" src="https://github.com/user-attachments/assets/cfc0d731-7b29-4702-9cf6-3da4ddf5f43e" />
</div>

## Optimizations for opt_check.v
<div align="center">
	<img width="900" height="90" alt="image" src="https://github.com/user-attachments/assets/47d91e2b-9ab8-420a-bc62-8f5ba5bc877e" />
	<img width="600" height="200" alt="image" src="https://github.com/user-attachments/assets/a1d9fd59-69d3-4055-9c93-18f85abb54bc" />
	<img width="939" height="500" alt="image" src="https://github.com/user-attachments/assets/31bc73cd-f881-4af1-bcb3-c15dceb6d3dd" />
</div>

## Optimizations for opt_check2.v
<div align="center">
	<img width="900" height="90" alt="image" src="https://github.com/user-attachments/assets/98194100-c254-41ab-8fff-e887a84c4e41" />
	<img width="600" height="300" alt="image" src="https://github.com/user-attachments/assets/8c6b5ca2-b483-4985-86ca-f261775e5bdc" />
	<img width="939" height="515" alt="image" src="https://github.com/user-attachments/assets/ad93fe26-3cc6-49b1-9db9-b56176f514e1" />
</div>

## Optimizations for opt_check3.v
<div align="center">
	<img width="836" height="102" alt="image" src="https://github.com/user-attachments/assets/8f2bb84d-44e9-4d19-be4d-b1c65e8587ea" />
	<img width="600" height="300" alt="image" src="https://github.com/user-attachments/assets/b11b1abf-6f7b-4a50-b3dd-208784a0ffec" />
	<img width="927" height="538" alt="image" src="https://github.com/user-attachments/assets/5ee4ec93-b72d-46bb-9106-9d4cb3e883d0" />
</div>

## Optimizations for opt_check4.v
<div align="center">
	<img width="867" height="89" alt="image" src="https://github.com/user-attachments/assets/004e1301-9a2c-4298-872f-9f9ea0e1e43f" />
	<img width="940" height="519" alt="image" src="https://github.com/user-attachments/assets/8a5e1caa-6203-4117-9820-cca452d83e4d" />
</div>

## Lab for Sequential Logic Optimizations
<div align="center">
    <img width="791" height="398" alt="image" src="https://github.com/user-attachments/assets/06d6eb1c-d687-4003-93fa-74c6e37ef59a" />
</div>

## Optimizations for dff_const1.v
<div align="center">
	<img width="500" height="106" alt="image" src="https://github.com/user-attachments/assets/bb1531c9-7bee-46c4-a162-c92248053969" />
	<img width="940" height="372" alt="image" src="https://github.com/user-attachments/assets/50b01b85-fb2c-4a92-b2ba-aeac16969d1e" />
    <img width="600" height="174" alt="image" src="https://github.com/user-attachments/assets/05705b3e-10f9-4b41-951a-001fbdf3f315" />
    <img width="940" height="469" alt="image" src="https://github.com/user-attachments/assets/614d8c40-27e8-4d26-84cd-69079c67bb19" />
</div>

## Optimizations for dff_const2.v
<div align="center">
	<img width="740" height="358" alt="image" src="https://github.com/user-attachments/assets/bc074db7-bf3e-4f09-852b-14d9a88bc248" />
	<img width="740" height="400" alt="image" src="https://github.com/user-attachments/assets/bd5c9dc0-e33a-4772-a62f-221452e833b1" />
</div>

## Optimizations for dff_const3.v
<div align="center">
	<img width="500" height="113" alt="image" src="https://github.com/user-attachments/assets/e8393bac-2ace-4605-988a-01b6464781f6" />
    <img width="740" height="357" alt="image" src="https://github.com/user-attachments/assets/8b65b606-249c-4635-8e67-e108248e3eae" />
    <img width="738" height="574" alt="image" src="https://github.com/user-attachments/assets/8c10b5be-0959-4cc7-8c9e-b49520c70309" />
    <img width="740" height="253" alt="image" src="https://github.com/user-attachments/assets/1835f763-ebb4-49de-bf49-9a63e1c6c8c2" />
</div>

## Optimizations for dff_const4.v
<div align="center">
	<img width="740" height="379" alt="image" src="https://github.com/user-attachments/assets/b58c6943-d7c3-4547-a2d1-a1508ddb1b59" />
    <img width="740" height="400" alt="image" src="https://github.com/user-attachments/assets/4daa4d16-6778-49e1-9aac-a2f94fe5a3bc" />
</div>

## Optimizations for dff_const5.v
<div align="center">
    <img width="740" height="382" alt="image" src="https://github.com/user-attachments/assets/80d39cb9-f47f-4fc6-bf9e-d5a3784f0e6b" />
	<img width="402" height="548" alt="image" src="https://github.com/user-attachments/assets/02e880ed-0630-4425-8fe0-fe187537b63e" />
    <img width="740" height="220" alt="image" src="https://github.com/user-attachments/assets/4c830601-516a-4bb7-a966-bf4defef47ac" />
</div>

## Sequential Optimizations for Unused Outputs
## Optimization of counter_opt.v
<div align="center">
	<img width="740" height="200" alt="image" src="https://github.com/user-attachments/assets/1ab44278-432f-4ea4-874c-8691fefe8379" />
    <img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/17e16d8c-b5b3-4174-ab0d-e4e8d2f661b4" />
    <img width="1046" height="365" alt="image" src="https://github.com/user-attachments/assets/5f2f718e-c9eb-41d4-9dd5-6b19b2364864" />
</div>

## Optimization of counter_opt2.v
<div align="center">
     <img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/16fb1266-4c35-468b-aed4-73e1584e777c" />
     <img width="940" height="330" alt="image" src="https://github.com/user-attachments/assets/020f0d5c-fd33-4832-9bb6-91eec54b67c1" />
</div>






