
# 🚀 VSDBabySoC: Synthesis and Gate-Level Simulation 

## 📚 Table of Contents
1. [Pre-Synthesis Functional Simulation Recap](#pre-synthesis-functional-simulation-recap)
2. [Synthesis: From RTL to Gates](#synthesis-from-rtl-to-gates)
3. [Post-Synthesis Simulation (GLS)](#post-synthesis-simulation-gls)

---

## 🧩 Pre-Synthesis Functional Simulation Recap

In this stage, the **VSDBabySoC** design was verified at **RTL level** to ensure correct logical functionality before synthesis. The simulation used **ideal, zero-delay conditions** to check that the verilog code accurately implemented the intended behavior, confirming functional correctness early in the design stage. 

### Week 2 Simulation Results

The pre-synthesis simulation confirmed that the **VSDBabySoC** integrating the **rvmyth** RiSC-V CPU core, executed its test proram correctly. The CPU's digital outputs were properly converted by the **DAC** into expected analog signals. This validated the design's intended funtionality and established a reference for comparing future post-synthesis results.

### Pre-Synthesis (RTL) Simulation Waveform
  
  <img width="900" height="300" alt="image" src="https://github.com/user-attachments/assets/dca20f2f-2d04-496b-bf73-230b5ba98952" /><br>
- To observe analog output in gtkwave
   - Right Click---> Out(signal)---> Data Format--->Analog--->Step

---

## 🔄 Synthesis: From RTL to Gates

**Synthesis** converts the RTL design into gate-level netlist made of standard cells from a target technology library. In this project, the **Yosys** tool and **Sky130 PDK** are used to perform this automated RTL-to-gates transformation.

- The entire synthesis workflow is automated using a Yosys script located at:
```
/VSDBabySoCProject/soc/VSDBabySoC/src/script/yosys.ys
```

## 🧭 Steps Involved in Synthesis   -

### Step 1: Reading Input Design Files

The first phase involves loading all Verilog source files that describe the design's behavior.

####
```tcl
read_verilog vsdbabysoc.v
```
- Loads the top-level Verilog file that defines the complete VSDBabySoC system. This file instantiates and connects all major components: the RISC-V core, PLL, DAC, and any glue logic.

####
```tcl
read_verilog -sv -I ../include ../../output/compiled_tlv/rvmyth.v
```
- Loads the `rvmyth` RISC-V CPU core, which is the computational heart of the SoC.
- `-I ../include`: Instructs Yosys to search the `../include` directory for any header files that `rvmyth.v` reference using `` `include`` directives.

####
```tcl
read_verilog -sv -I ../include clk_gate.v
```
- Loads the clock gating logic, which is used to disable clock signals to inactive portions of the circuit to save power.
- `-I ../include`: Ensures any dependencies are resolved from the include directory
---

### Step 2: Reading Technology Libraries

Before synthesis can begin, Yosys needs detailed information about the physical characteristics of the available standard cells and macros. This information is provided in **Liberty (.lib)** format files.

####
```tcl
read_liberty -lib ../lib/avsdpll.lib
```
- Loads the timing, power, and functional characteristics of the Analog Voltage Scaled Digital Phase-Locked Loop (PLL) macro.

####
```tcl
read_liberty -lib ../lib/avsddac.lib
```

- Loads the characterization data for the Analog Voltage Scaled Digital-to-Analog Converter (DAC).

####
```tcl
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
- Loads the complete SKY130 High-Density standard cell library for **typical** process corner, **25°C** temperature, and **1.8V** supply voltage.

---

### Step 3: High-Level Synthesis

This is where the actual transformation from RTL to logic begins.

####
```tcl
synth -top vsdbabysoc
```
- Executes the main synthesis flow. Converts the RTL code into a synthesized design.

--

### Step 4: Technology Mapping

Now we map the generic logic to actual physical cells from the SKY130 library.

####
```tcl
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
- Maps all generic D flip-flops (`$dff` cells) inferred during synthesis to actual flip-flop implementations from the SKY130 library.

####
```tcl
opt
```
- Runs a series of optimization passes on the partially mapped design.

####
```tcl
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
- This is the **core technology mapping step** where combinational logic is mapped to actual SKY130 gates.
- This single command determines the area, delay, and power of your entire synthesized design. The quality of ABC's mapping directly impacts chip performance.

---

### Step 5: Netlist Finalization

After mapping is complete, the netlist needs to be cleaned up and prepared for output.

####
```tcl
flatten
```
- Removes all hierarchical boundaries, creating a single flat module containing all standard cells.
- To view the hierarchical design we can use `show vsdbabysoc` before the `flatten` command.

####
```tcl
setundef -zero
```

- Forces all signals with undefined (`x`) values to logic zero.

####
```tcl
clean -purge
```
- Performs a final, aggressive cleanup of the netlist.

####
```tcl
stat
```
- Generates a detailed report of the synthesized design.

####
```tcl
write_verilog -noattr ../../output/synth/vsdbabysoc.synth.v
```
- Exports the final synthesized netlist to a Verilog file.
- `-noattr`: Suppresses Yosys-specific attributes from being written to the file

<img width="700" height="300" alt="image" src="https://github.com/user-attachments/assets/ee64c48e-cc98-466e-80c5-79101adf1697" /><br><br>
<img width="700" height="50" alt="image" src="https://github.com/user-attachments/assets/344caa11-b5db-4002-ba36-a97718e5ec09" /><br><br>
<img width="700" height="300" alt="image" src="https://github.com/user-attachments/assets/8779999b-1532-423c-a449-0eb26778e517" /><br><br>
<img width="402" height="300" alt="image" src="https://github.com/user-attachments/assets/c6ed313d-f844-4bd0-8aeb-cb751534d6b4" /><br><br>
<img width="466" height="350" alt="image" src="https://github.com/user-attachments/assets/15071508-c760-4dbd-aef2-048b02d77afc" /><br><br>
<img width="449" height="300" alt="image" src="https://github.com/user-attachments/assets/5c777b9b-8d0b-4fa5-b74d-ee31f62db16b" /><br><br>
<img width="418" height="300" alt="image" src="https://github.com/user-attachments/assets/a9191fda-319c-4930-8446-e70c29827f79" /><br><br>
<img width="800" height="300" alt="image" src="https://github.com/user-attachments/assets/023fa2a1-ddeb-4f0d-9057-7ff862a3c18d" /><br><br>
<img width="700" height="80" alt="image" src="https://github.com/user-attachments/assets/78b004a6-46d4-40a7-9cfd-19093c957b94" /><br>
<img width="250" height="40" alt="image" src="https://github.com/user-attachments/assets/9d75a277-6dcc-46e9-8066-0272e55410f6" />


**The primary output of synthesis** will be used for:
- Post-synthesis simulation (Gate-Level Simulation)
- Static Timing Analysis (STA)
---

## 🧩 Post-Synthesis Simulation (GLS)

### What is Post-Synthesis Simulation?
**Post-synthesis simulation**, also known as **Gate-Level Simulation (GLS)** is the verification step performed after synthesis to ensure that the gate-level netlist (generated by tools like Yosys) still behaves functionally and temporally correct, just like the original RTL design. GLS uses the actual standard cell implementations from the technology library (SKY130).

## ⚙️ Purpose

- To verify that the synthesized gate-level design (netlist) preserves the same logical behavior as the RTL.
- To check the impact of real gate delays introduced by the synthesis process.
- To confirm that no timing or functional issues were introduced during logic optimization or technology mapping.

## 🧠 How It Works

- The synthesized netlist replaces the RTL code.
- The testbench (same as in pre-synthesis simulation) applies inputs.
- The simulator uses real gate-level delays (from .lib or .sdf) to model realistic timing behavior.
- Output waveforms are compared to the pre-synthesis reference.
  
**Key characteristics:**
- **Structural simulation:** Simulates the actual gates and flip-flops that will be fabricated on silicon
- **Technology-specific:** Uses models from the SKY130 PDK that match the physical characteristics of manufactured chips

### ✅Expected Outcomes

- Confirms functional equivalence between RTL and gate-level design.
- Identifies any timing violations or glitches introduced after synthesis.
- Generates waveforms showing realistic timing behavior.

<img width="900" height="400" alt="image" src="https://github.com/user-attachments/assets/d0995cf6-09d7-4a5b-99e2-f85a3d26d45b" /> <br><br>

 <img width="940" height="534" alt="image" src="https://github.com/user-attachments/assets/846249a2-264a-4b14-a6e8-1270993efaaa" /><br>

**Explanation**:
- -DPOST_SYNTH_SIM: set to true for compile/simulation run
- -I ../include and ../module ----> Include paths for header and modules
- -o output/post_synth_sim/post_synth_sim.out ----> Location of output
  
----

## 🌟 Importance of Post-Synthesis Simulation

- Post-synthesis simulation is a crucial step in the digital design flow because it verifies that the synthesized (gate-level) version of the circuit still behaves correctly and meets timing requirements — just like the original RTL design.
- GLS serves as a critical validation checkpoint in the digital design flow. Here's why it's indispensable:

### 🧩 1. Ensures Functional Equivalence

- After synthesis, your RTL code is converted into a gate-level netlist made of standard cells.
- Post-synthesis simulation verifies that logic optimizations or resource sharing done by the synthesis tool haven’t changed the intended functionality.
  
✅ Ensures that “what you built” is the same as “what you designed.”


### ⚙️ 2. Verifies Timing Behavior

- Unlike RTL simulation (which assumes zero delay), gate-level simulation includes real propagation delays from the standard cell library or SDF file.
- This helps check for setup, hold, or glitch-related issues due to signal timing.
  
✅ Confirms the design works correctly under realistic timing conditions.

### 🧠 3. Detects Synthesis-Introduced Issues

- Sometimes synthesis tools modify or optimize the logic in ways that might introduce:
- Unintended logic inversions
- Mismatched reset or clock behavior
- Missing signals due to constant propagation
  
✅ Post-synthesis simulation helps catch these synthesis-induced bugs early.

### 🧾 4. Validates Testbench Reusability

- The same testbench used in pre-synthesis (RTL) simulation is applied to the gate-level design.
- If both pass with the same output, it confirms testbench correctness and consistency.

✅ Assures your verification setup is solid.

### ⏱️ 5. Builds Confidence Before Physical Design

- Successful post-synthesis simulation gives confidence that the netlist is functionally correct before moving on to:
- Static Timing Analysis (STA)
- Placement & Routing (P&R)
  
✅ Reduces the risk of discovering functional errors late in the design flow.

---

## 🧩 Pre-Synthesis vs. Post-Synthesis Simulation

| **Aspect** | **Pre-Synthesis Simulation (RTL)** | **Post-Synthesis Simulation (GLS)** |
|------------|-------------------------------------|--------------------------------------|
| **Design Level** | RTL | Gate-level netlist |
| **Abstraction Level** | Abstract: `always` blocks, `if-else`, arithmetic operators | Concrete: AND gates, OR gates, flip-flops, multiplexers |
| **Simulation Type** | Functional Simulation (Zero-delay, ideal) | Timing Simulation (real gate delays from .lib) |
| **Delay Information** | No real delay information; focuses on logical correctness | Includes setup/hold times, propagation delays, clock-to-Q delays |
| **Primary Goal** | Verify functional and logical correctness of the RTL code | Performnace, timing and area optimization |
| **Errors Detected** | Logic bugs, FSM errors, algorithmic mistakes, incorrect protocol implementation | Synthesis-induced bugs, timing violations, glitches, race conditions, X-propagation |
| **Models Used** | RTL Verilog files written by designer | Standard cell Verilog models from foundry (e.g., `sky130_fd_sc_hd.v`) |
| **Output Accuracy** | Logically correct but timing-optimistic | More accurate representation of actual silicon behavior |
| **Tools Used** | Verilog Simulator (iverilog, Modelsim) | Yosys (synthesis), OpenSTA (timing) |
---

## ⚙️ Gate-Level Simulation 

The GLS process involves several preparatory steps followed by compilation and execution of the simulation.

---

#### Step 1: Copy Required Library Files

Before simulation, we need to gather all necessary files into the working directory.

##### Copy Standard Cell Verilog Models
```bash
sky130RTLDesignAndSynthesisWorkshop/my_lib/verilog_model/sky130_fd_sc_hd.v 
```
- This file contains the **behavioral Verilog descriptions** for every standard cell in the SKY130 High-Density library.

##### Copy Primitives Library
```bash
sky130RTLDesignAndSynthesisWorkshop/my_lib/verilog_model/primitives.v 
```
- This file defines low-level **primitive building blocks** used within the standard cell models.

##### Copy Synthesized Netlist
```bash
VSDBabySoCProject/soc/VSDBabySoC/output/synth/vsdbabysoc.synth.v 
```
- Copies the gate-level netlist (output of Yosys) into the directory where simulation will be run.

---

#### Step 2: Compile the Testbench

##### Compile with Icarus Verilog
```bash
iverilog -o VSDBabySoc/soc/VSDBabySoC/output/post_synth_sim/post_synth_sim.out \
    -DPOST_SYNTH_SIM \
    -DFUNCTIONAL \
    -DUNIT_DELAY=#1 \
    -I  VSDBabySoCProject/soc/VSDBabySoC/src/include \
    -I VSDBabySoCProject/soc/VSDBabySoC/src/module \
    VSDBabySoCProject/soc/VSDBabySoC/src/testbench.v
```
- Compiles all Verilog files into a single executable simulation binary.

**Detailed flag explanation:**

##### `-o  VSDBabySoCProject/soc/VSDBabySoC/output/post_synth_sim/post_synth_sim.out`
- Output file name
- Specifies the name and location of the compiled executable
- Without this flag, the default output would be `a.out` in the current directory

##### `-DPOST_SYNTH_SIM`
- Define a preprocessor macro named `POST_SYNTH_SIM` used in the testbench for conditional compilation
- When this macro is defined, the testbench includes the synthesized netlist else it includes the RTL code
- This allows the same testbench to be used for both pre- and post-synthesis simulation

##### `-DFUNCTIONAL`
- Define a macro named `FUNCTIONAL`
- Tells the SKY130 cell models to run in **functional mode** rather than full timing mode
- This simplifies the synthesis without worrying about the timings checks

##### `-DUNIT_DELAY=#1`
- Define a macro that sets a uniform delay of `#1` time unit for all gates
- Every gate in the design will have a propagation delay of 1 time unit

##### `-I VSDBabySoCProject/soc/VSDBabySoC/src/include`
- Add include directory to search path
- When the testbench has `` `include .vh``, Verilog will look in this directory

##### `-I VSDBabySoCProject/soc/VSDBabySoC/src/module`
- Add module directory to search path
- Iverilog can automatically find and compile included verilog files

##### `VSDBabySoCProject/soc/VSDBabySoC/src/testbench.v`
- The top-level file to compile
- Iverilog starts here and recursively compiles all dependencies

---

#### Step 3: Run the Simulation

##### Navigate to Output Directory
```bash
cd VSDBabySoCProject/soc/VSDBabySoC/output/post_synth_sim/
```
- Move to the directory where the simulation executable resides.

##### Execute Simulation
```bash
./post_synth_sim.out
```
- Runs the compiled simulation executable.

---

#### Step 4: View Waveforms with GTKWave

##### Open Waveform Viewer
```bash
gtkwave post_synth_sim.vcd
```
- Launches the GTKWave waveform viewer to visually inspect simulation results.<br>

<img width="850" height="305" alt="image" src="https://github.com/user-attachments/assets/c02f6463-919e-4e69-ae6a-708461294686" /><br><br>
<img width="800" height="434" alt="image" src="https://github.com/user-attachments/assets/846e18b5-8edd-4f37-b6b7-7b0e3ac375c3" />

*The above waveform shows the VSDBabySoC behavior after synthesis, with realistic gate delays included.*

---

### Waveform Analysis and Comparison

#### Functional Correctness Verification ✅

The primary objective of post-synthesis simulation is to confirm that the synthesized gate-level netlist maintains the same functional behavior as the original RTL design.

* **Analyzing the recieved output** -
  1. **`reset`**: The simulation begins with `reset` held **high** for a few microseconds. This correctly initializes the system. Once `reset` goes **low**, the processor starts executing its program.
  2. **`CLK`**: This is the main system clock, generated by the PLL. It appears to be a stable, periodic square wave.
  3. **`RV_TO_DAC[9:0]`**: This is the 10-bit digital output from the RISC-V core. A repeating pattern of changing bits. This pattern represents the sequence of numbers the processor is sending to the DAC.
  4. **`VREFH`**: This is the high reference voltage for the DAC. As expected, it is a **constant DC value**, represented by the flat line at the top.
  5. **`OUT`** (Analog Output): This signal is an analog waveform that directly mirrors the digital pattern from `RV_TO_DAC`. It is a periodic periodic signal. 

---

#### Comparison Summary Table

| **Aspect** | **Pre-Synthesis (RTL) Simulation** | **Post-Synthesis (GLS) Simulation** |
|------------|-------------------------------------|--------------------------------------|
| **Functional Behavior** | ✅ Correct waveform, incrementing and then decrementing digital values | ✅ Identical functional behavior maintained |
| **Signal Values** | Match expected sequence | Match expected sequence (same as RTL) |
| **Waveforms** | <img width="900" height="473" alt="image" src="https://github.com/user-attachments/assets/419b06d2-8c67-4149-9b6b-82ced090f558" /> | <img width="900" height="534" alt="image" src="https://github.com/user-attachments/assets/846e18b5-8edd-4f37-b6b7-7b0e3ac375c3" /> |
 |

---
