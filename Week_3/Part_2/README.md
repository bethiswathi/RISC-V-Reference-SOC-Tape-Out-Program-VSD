## Fundamentals of STA

## 🧠 What is STA (Static Timing Analysis)?

**Static Timing Analysis (STA)** is a method of validating the timing performance of a digital circuit without using test vectors.
- It checks whether signals in a design arrive at the correct time — ensuring that data is properly captured by flip-flops or memory elements.
- It’s called “static” because it analyzes all possible paths using the design’s timing constraints and clock definitions, rather than simulating actual inputs.

## ⚙️ Basic Idea

STA computes timing delays across all paths from:

- Clock → Flip-flop
- Flip-flop → Flip-flop
- Input → Flip-flop
- Flip-flop → Output
- Input → Output

It then checks if setup and hold constraints are satisfied for each timing path.

## 🔗 Key Terms in STA

| Term | Description |
|------|-------------|
| **Timing Path** |	A path that data travels from a startpoint (launch) to an endpoint (capture) |
| **Startpoint** |	Typically a flip-flop output (Q) or input port |
| **Endpoint** |	Typically a flip-flop input (D) or output port |
| **Clock Path** |	The route the clock signal takes to reach flip-flops |
| **Data Path** |	The route that data takes from one register to another |
| **Setup Time** |	Minimum time before the clock edge that data must be stable |
| **Hold Time** |	Minimum time after the clock edge that data must remain stable |
| **Clock Skew** |	Difference in arrival times of the same clock at two points |
| **Slack** |	Difference between required time and arrival time (margin) |
| **Critical Path** |	The longest delay path (smallest positive or most negative slack) |


## 🧩 STA Flow (Step-by-Step)

| Step                         | Description                                                                                 |
| ---------------------------- | ------------------------------------------------------------------------------------------- |
| **1. Input Preparation**     | Provide synthesized **netlist**, **timing constraints (SDC)**, and **cell library (.lib)**. |
| **2. Path Identification**   | Tool finds all possible **timing paths** between startpoints and endpoints.                 |
| **3. Delay Calculation**     | Calculates **cell delay** (gate delay) + **net delay** (interconnect delay).                |
| **4. Setup and Hold Checks** | Compares **arrival time** vs **required time** for each endpoint.                           |
| **5. Slack Computation**     | Calculates **slack = required time − arrival time**.                                        |
| **6. Report Generation**     | Produces timing reports (e.g., worst setup/hold violations).                                |


## ⏱️ Two Main Timing Checks
| Type                 | Checks                                            | Violation When                                   |
| -------------------- | ------------------------------------------------- | ------------------------------------------------ |
| **Setup Time Check** | Data must arrive **before** the active clock edge | Data arrives **too late** (negative setup slack) |
| **Hold Time Check**  | Data must remain **stable after** the clock edge  | Data changes **too early** (negative hold slack) |


## 🧰 Inputs Required for STA
| Input                         | Description                                              |
| ----------------------------- | -------------------------------------------------------- |
| **Netlist (.v)**              | Post-synthesis gate-level description                    |
| **Liberty file (.lib)**       | Contains delay and constraint info of each standard cell |
| **SDC file**                  | Defines clocks, input/output delays, constraints         |
| **Parasitics (.spef / .sdf)** | Interconnect delay information (post-layout)             |
| **STA tool**                  | Example: **OpenSTA**, **PrimeTime**, etc.                |



## 🧭 STA Output

- Timing Reports (setup, hold, clock skew)
- Critical Path List
- Worst Negative Slack (WNS)
- Total Negative Slack (TNS)
- Clock Frequency Margin

## ⚡ Example Tools

| Tool                   | Type        | Description                              |
| ---------------------- | ----------- | ---------------------------------------- |
| **OpenSTA**            | Open-source | Used with OpenROAD for open-source flows |
| **Synopsys PrimeTime** | Commercial  | Industry-standard STA tool               |
| **Cadence Tempus**     | Commercial  | Advanced STA and signoff                 |

## 🧩 Setup and Hold Checks

- Both are two most fundamental timing checks in Static Timing Analysis (STA).
- These checks ensure that data is correctly launched, propagated, and captured by flip-flops in sync with the clock.









## 📊 Summary: Setup vs Hold Check

| Feature            | **Setup Check**                            | **Hold Check**                                  |
| ------------------ | ------------------------------------------ | ----------------------------------------------- |
| **Purpose**        | Ensure data arrives *before* capture edge  | Ensure data remains stable *after* capture edge |
| **When checked**   | Across *different* clock cycles            | Within the *same* clock cycle                   |
| **Violation**      | Data arrives **too late**                  | Data arrives **too early**                      |
| **Impact**         | Limits **max frequency**                   | Causes **functional error**                     |
| **Fix**            | Speed up data path / increase clock period | Add delay to data path / adjust skew            |
| **Slack formula**  | (Clock period − Setup time) − Data delay   | Data delay − Hold time                          |
| **Clock relation** | Usually opposite edges (launch & capture)  | Same edge                                       |







  
 Focus on: 
o Setup and Hold checks 
o Slack 
o Clock definitions 
o Path-based analysis 
Deliverable: 
A one-page summary or key notes from the STA course (bullet points are fine).
