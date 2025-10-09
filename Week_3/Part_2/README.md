## Fundamentals of STA

### 🧠 What is STA (Static Timing Analysis)?

**Static Timing Analysis (STA)** is a method of validating the timing performance of a digital circuit without using test vectors.
- It checks whether signals in a design arrive at the correct time — ensuring that data is properly captured by flip-flops or memory elements.
- It’s called “static” because it analyzes all possible paths using the design’s timing constraints and clock definitions, rather than simulating actual inputs.

### ⚙️ Basic Idea

STA computes timing delays across all paths from:

- Clock → Flip-flop
- Flip-flop → Flip-flop
- Input → Flip-flop
- Flip-flop → Output
- Input → Output

It then checks if setup and hold constraints are satisfied for each timing path.
<br><br>
### 🔗 Key Terms in STA

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

<br>

### 🧩 STA Flow (Step-by-Step)

| Step                         | Description                                                                                 |
| ---------------------------- | ------------------------------------------------------------------------------------------- |
| **1. Input Preparation**     | Provide synthesized **netlist**, **timing constraints (SDC)**, and **cell library (.lib)**. |
| **2. Path Identification**   | Tool finds all possible **timing paths** between startpoints and endpoints.                 |
| **3. Delay Calculation**     | Calculates **cell delay** (gate delay) + **net delay** (interconnect delay).                |
| **4. Setup and Hold Checks** | Compares **arrival time** vs **required time** for each endpoint.                           |
| **5. Slack Computation**     | Calculates **slack = required time − arrival time**.                                        |
| **6. Report Generation**     | Produces timing reports (e.g., worst setup/hold violations).                                |

<br>

### ⏱️ Two Main Timing Checks

| Type                 | Checks                                            | Violation When                                   |
| -------------------- | ------------------------------------------------- | ------------------------------------------------ |
| **Setup Time Check** | Data must arrive **before** the active clock edge | Data arrives **too late** (negative setup slack) |
| **Hold Time Check**  | Data must remain **stable after** the clock edge  | Data changes **too early** (negative hold slack) |

<br>

### 🧰 Inputs Required for STA

| Input                         | Description                                              |
| ----------------------------- | -------------------------------------------------------- |
| **Netlist (.v)**              | Post-synthesis gate-level description                    |
| **Liberty file (.lib)**       | Contains delay and constraint info of each standard cell |
| **SDC file**                  | Defines clocks, input/output delays, constraints         |
| **Parasitics (.spef / .sdf)** | Interconnect delay information (post-layout)             |
| **STA tool**                  | Example: **OpenSTA**, **PrimeTime**, etc.                |

<br>

### 🧭 STA Output

- Timing Reports (setup, hold, clock skew)
- Critical Path List
- Worst Negative Slack (WNS)
- Total Negative Slack (TNS)
- Clock Frequency Margin

<br>

### ⚡ Example Tools

| Tool                   | Type        | Description                              |
| ---------------------- | ----------- | ---------------------------------------- |
| **OpenSTA**            | Open-source | Used with OpenROAD for open-source flows |
| **Synopsys PrimeTime** | Commercial  | Industry-standard STA tool               |
| **Cadence Tempus**     | Commercial  | Advanced STA and signoff                 |

<br>

## 🧩 Setup and Hold Checks

- Both are two most fundamental timing checks in Static Timing Analysis (STA).
- These checks ensure that data is correctly launched, propagated, and captured by flip-flops in sync with the clock.

### ⚙️ 1️⃣ Setup Time Check
### 🔹 What is Setup Time?

- Setup Time is the minimum time before the clock edge during which the data input (D) of a flip-flop must be stable so that it can be reliably latched on the active clock edge.

- If the data arrives too late, it violates the setup time requirement.

### 🧩 Setup Check Condition

Data launched by one flip-flop (FF1) must reach the destination flip-flop (FF2) before FF2’s clock edge that captures it.
```
Clock period ≥ (Launch clock delay + Data path delay + Setup time) − Capture clock delay
````

### 📉 Setup Violation

| Cause                  | Fix                                    |
| ---------------------- | -------------------------------------- |
| Long data path delay   | Optimize combinational logic           |
| Large setup time       | Use faster flip-flop                   |
| Clock skew unfavorable | Use **useful skew** or clock balancing |
| High fanout/load       | Buffer insertion or sizing             |


### ⚙️ 2️⃣ Hold Time Check
### 🔹 What is Hold Time?

- Hold Time is the minimum time after the active clock edge during which the input data (D) must remain stable.

- If data changes too early, it violates the hold time.

### 🧩 Hold Check Condition

Data from FF1’s output must not arrive at FF2’s input too soon after FF2’s clock edge.
````
Data path delay ≥ (Hold time + Capture clock delay − Launch clock delay)

````

### 📉 Hold Violation

| Cause                      | Fix                           |
| -------------------------- | ----------------------------- |
| Short data path delay      | Add delay (buffers/inverters) |
| Clock skew (negative skew) | Adjust clock tree balance     |
| Too-fast cells             | Replace with slower cells     |


### 📊 Summary: Setup vs Hold Check

| Feature            | **Setup Check**                            | **Hold Check**                                  |
| ------------------ | ------------------------------------------ | ----------------------------------------------- |
| **Purpose**        | Ensure data arrives *before* capture edge  | Ensure data remains stable *after* capture edge |
| **When checked**   | Across *different* clock cycles            | Within the *same* clock cycle                   |
| **Violation**      | Data arrives **too late**                  | Data arrives **too early**                      |
| **Impact**         | Limits **max frequency**                   | Causes **functional error**                     |
| **Fix**            | Speed up data path / increase clock period | Add delay to data path / adjust skew            |
| **Slack formula**  | (Clock period − Setup time) − Data delay   | Data delay − Hold time                          |
| **Clock relation** | Usually opposite edges (launch & capture)  | Same edge                                       |

<br>

## ⚙️ What is Slack?

- Slack is one of the most important concepts in Static Timing Analysis (STA) because it tells you whether your circuit meets timing requirements or not
  
- Slack is the difference between the required time and the arrival time of a signal at a timing endpoint.
  
- In simpler words:

#### 🧭 Slack = Required Time − Arrival Time

It tells how much “timing margin” you have — whether your signal is early enough (positive slack ✅) or too late (negative slack ❌).
<br><br>

### 🧩 Meaning of Slack Values

| Slack Value      | Interpretation                            | Result                     |
| ---------------- | ----------------------------------------- | -------------------------- |
| **Positive (+)** | Data arrives early (before required time) | ✅ Timing is met            |
| **Zero (0)**     | Data arrives exactly on time              | ⚠️ Marginal but acceptable |
| **Negative (−)** | Data arrives too late (misses timing)     | ❌ Timing violation         |

<br>

## 🧮 Types of Slack 

- There are two main types of slack corresponding to setup and hold checks.
   - Setup Slack
   - Hold Slack

### 1️⃣ Setup Slack

- Checks late arrival (data must arrive before next clock edge)
- Computed over two consecutive clock cycles

#### Formula:
```
Setup Slack = (Clock Period - Setup Time) - Datapath Delay

```

### 2️⃣ Hold Slack

- Checks early arrival (data must not change too soon)
- Computed within the same clock edge

#### Formula:
```
Hold Slack = Datapath Delay - Hold Time

```

### 📊 Summary Table

| Aspect         | **Setup Slack**                           | **Hold Slack**               |
| -------------- | ----------------------------------------- | ---------------------------- |
| Checks         | Data arrives **too late**                 | Data arrives **too early**   |
| Time Window    | Across **two clock edges**                | Within **same clock edge**   |
| Affected by    | Clock period, data path delay, setup time | Data path delay, hold time   |
| Violation Type | **Max delay** violation                   | **Min delay** violation      |
| Typical Fix    | Speed up data path / adjust clock         | Add buffers / slow down path |

<br>

### 📈 Related STA Metrics

| Metric                         | Meaning                                                       |
| ------------------------------ | ------------------------------------------------------------- |
| **WNS (Worst Negative Slack)** | The most negative slack in the design (worst violation).      |
| **TNS (Total Negative Slack)** | Sum of all negative slacks — measures overall timing quality. |
| **TNS = 0 and WNS ≥ 0**        | ✅ Means design meets all timing requirements.                 |

<br>

## 🕒 What is a Clock in STA?

- In STA, a clock defines:
- When signals are launched (sent) and captured (received).
- The timing reference for all sequential elements (flip-flops, latches, etc.).
- The frequency, duty cycle, and waveform of operation.
- So, a clock definition tells the STA tool everything it needs to analyze timing paths correctly.

### ⚙️ Clock Definition Components

| Parameter                | Description                                             |
| ------------------------ | ------------------------------------------------------- |
| **Clock Name**           | A unique identifier (e.g., `clk_main`)                  |
| **Source Port / Pin**    | The signal or pin that carries the clock                |
| **Period**               | Time for one full clock cycle (e.g., 10 ns for 100 MHz) |
| **Waveform**             | Defines rising and falling edges (used for duty cycle)  |
| **Edge Polarity**        | Rising or falling edge triggering                       |
| **Generated Clock**      | Derived clocks from dividers, muxes, or PLLs            |
| **Uncertainty / Jitter** | Variations in clock arrival time                        |
| **Skew**                 | Delay difference between launch and capture flip-flops  |

<br>

### 🧠 Why Clock Definition is Important

STA tools (like OpenSTA, PrimeTime, etc.) need to know:
- Which paths are clocked (sequential) and which are combinational.
- When data is launched and captured.
- How to compute setup and hold slacks.

 Without defining clocks, STA cannot perform timing analysis.


### 🧩 Defining Clocks in STA (SDC Format)

In STA, we define clocks using commands in the SDC (Synopsys Design Constraints) file.

### ✅ 1️⃣ Primary Clock Definition

This defines the main input clock that drives flip-flops directly.

#### Example:
```
create_clock -name clk -period 10 [get_ports clk]

```
#### Explanation:

- -name clk → Clock name
- -period 10 → Clock period = 10 ns (100 MHz)
- [get_ports clk] → The clock signal comes from the input port clk

### ✅ 2️⃣ Clock Waveform Definition

By default, STA assumes a 50% duty cycle (rising edge at 0 ns, falling edge at period/2).
You can specify custom waveforms:
#### Example:
```
create_clock -name sys_clk -period 20 -waveform {0 8} [get_ports sys_clk]

```
#### Meaning:

- Period = 20 ns (50 MHz)
- Rising edge = 0 ns
- Falling edge = 8 ns → → 40% duty cycle

### ✅ 3️⃣ Generated Clock Definition

Used when the clock is derived from another clock — e.g., via a divider, PLL, or clock gate.

#### Example:
```
create_generated_clock -name div_clk -divide_by 2 \-source [get_ports clk] [get_pins u_divider/clk_out]
```
#### Explanation:

- -divide_by 2 → Frequency divided by 2
- -source [get_ports clk] → Derived from the main clock
- [get_pins u_divider/clk_out] → The output pin where the new clock appears


### ✅ 4️⃣ Virtual Clock Definition

A virtual clock is used when no physical clock port exists — e.g., for input/output timing of external interfaces.

#### Example:
```
create_clock -name virt_clk -period 10

```
Then, it’s used for input/output constraints:
```
set_input_delay 2 -clock virt_clk [get_ports data_in]
set_output_delay 3 -clock virt_clk [get_ports data_out]

```

### ✅ 5️⃣ Clock Uncertainty

Accounts for clock jitter or variation (timing margin).
```
set_clock_uncertainty 0.2 [get_clocks clk]
```
- Adds ±0.2 ns uncertainty to setup/hold calculations.


### ✅ 6️⃣ Clock Latency and Skew

**Clock Latency**: Time taken for the clock signal to reach a flip-flop from its source.
```
set_clock_latency 1.0 [get_clocks clk]
```

**Clock Skew**: Difference in clock arrival between launch and capture flops — STA tools calculate this automatically but you can also constrain it.


### 📊 Types of Clocks Summary

| Type                | Description                             | Example                          |
| ------------------- | --------------------------------------- | -------------------------------- |
| **Primary Clock**   | Comes from an external source           | `create_clock`                   |
| **Generated Clock** | Derived internally (divider, PLL, etc.) | `create_generated_clock`         |
| **Virtual Clock**   | Used for external timing (I/O)          | `create_clock` without a source  |
| **Gated Clock**     | Uses logic to enable/disable clock      | Often modeled as generated clock |

<br>

### 🧠 Quick Recap

| Concept             | Description                          |
| ------------------- | ------------------------------------ |
| **Clock period**    | Defines circuit speed (f = 1/period) |
| **Duty cycle**      | Ratio of high time to total period   |
| **Clock skew**      | Delay difference between flip-flops  |
| **Clock jitter**    | Random variation in clock edge       |
| **Uncertainty**     | Margin to cover skew + jitter        |
| **Generated clock** | Derived version of a parent clock    |

<br>








