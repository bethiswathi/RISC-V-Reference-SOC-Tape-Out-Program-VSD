# Timing libs, Hierachical vs Flat synthesis and Efficient Flop Coding Styles

## Introduction to Timing .libs
Libraries are characterized based on PVT conditions
- Process --> Variations due to fabrication
- Voltage --> Variations due to voltage
- Temperature --> Variations due to temperature

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

## Why stacking PMOS is bad
In CMOS design,stacked PMOS transistors(two or more PMOS connected in series, as in pull-up networks for logic like NAND gates) are often considered **bad** comopared to stacked NMOS because of the following reasons:
- Poor drive strength(high resistance):
   - PMOS devices already have lower mobility of holes compared to electrons in NMOS.
   - When you stack multiple PMOS in series, their effective resistance increases further, making the pull-up path weaker and slower.
- Slower switching speed :
   - Because of the higher reistance and reduced current drive, the rising transition(0 to 1) takes longer when multiple PMOS are stacked.
   - This limits performance, especially in gates with more inputs (like NOR gates).   

### <ins>**Flat Synthesis**</ins> 
Flat Synthesis removes hierachy, allowing global optimizations and potentially better performance/area but increases complexity and runtime. 
<div align="center">
  <img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/25d3e970-6d9a-47f9-8527-3de4af01f92f" />
</div>
command to write flat netlist

- flatten 

## Sub-Module Level Synthesis
Sub module level synthesis optimizes each module individually balancing performance, area and power within its scope.

### Importance of Sub-module level synthesis
Sub-module level synthesis is necessary because 

- Scalability: large massive designs are too big to synthesize flatty. Breaking them into sub-modules makes them manageable.
- Faster Turn-around: Each block can be synthesized,verified and iterated independently, reducing the compile time.
- Reuse of IPs: Pre synthesized/verified sub-modules( like ALUs,memories,controllers) can be reused across multiple designs.
- Debug & ECO ease: Errors can be fixed at sub-module level without re-running synthesis for the full chip.
- Parallel Processing: Different sub-modules can be synthesized concurrently, improving efficiency.
        
<div align="center">
  <img width="600" height="350" alt="image" src="https://github.com/user-attachments/assets/ea91b2c9-ebfb-4c87-a21c-94e7dd3439df" />
  <img width="600" height="150" alt="image" src="https://github.com/user-attachments/assets/65ffd506-bc83-44ea-a6f4-ee12c9a570b2" />
  <img width="600" height="350" alt="image" src="https://github.com/user-attachments/assets/b847dc62-07f1-47df-a39e-77cffc3b445e" />
  <img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/f8339686-55d1-4fce-92c1-9ca013fb92cb" />
  <img width="600" height="300" alt="image" src="https://github.com/user-attachments/assets/31a5ecbb-ca32-429d-8edb-d00e9dc0d427" />
</div>


## Various Flop Coding Styles and Optimization
Different coding styles exist because different design requirements demand different behaviors. Certain flop styles reduce switching or leakage for low-power designs. Some styles are faster or better for critical timing paths. Different flop styles give flexibility to meet functional, timing, power and test requirements.

Glitches occur in digital circuits due to signal delays, noise or timing issues. Flip flops avoid glitches by sampling the inputs only on the active clock edge. They provide synchronization, state retention and timing control in digital circuits.
  
<div align="center">
   <img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/21bc425e-2e08-46d3-9c72-88d5284f4dfc" />
</div>

## Different Types of Flops
set and reset are used to initialize the flops which can be synchronous and asynchronous. 
<div align="center">
   <img width="500" height="200" alt="image" src="https://github.com/user-attachments/assets/493a5629-a0a5-4ebd-8de7-5dfd125621d5" />
</div>

<div align="center">
   <img width="807" height="581" alt="image" src="https://github.com/user-attachments/assets/cdda1177-34ea-4727-857e-cc2fee5fe546" />
</div>

## DFF with Asynchronous Reset
The screenshot below shows DFF with asynchronous reset simulation in iverilog and waveform in gtkwave. Irrespective of clock and d, as soon as async_reset=1, q=0

<div align="center">
   <img width="700" height="350" alt="image" src="https://github.com/user-attachments/assets/cdf411b3-7d59-4fb8-96a3-a0c054bfa361" />
   <img width="700" height="300" alt="image" src="https://github.com/user-attachments/assets/c09c33ba-288b-46d0-b8c7-64b21ecd2aec" />
</div>

The commands to <ins>**synthesize DFF with asynchronous reset**</ins> are 
<div align="left">
   <img width="500" height="130" alt="image" src="https://github.com/user-attachments/assets/207314a4-0625-47a9-88b5-1b947db52489" />
</div>

<div align="center">
    <img width="940" height="535" alt="image" src="https://github.com/user-attachments/assets/5dd85e87-aaad-4d2b-8bac-f3255c5b35e0" />
</div>

The screenshot below shows the <ins>**synthesis of synchronous reset**</ins> 
<div align="center">
   <img width="940" height="530" alt="image" src="https://github.com/user-attachments/assets/d73f1af9-5290-4c7d-9293-64eae5f0403c" />
</div>

## Synthesizing mult2

<div align="center">
   <img width="886" height="530" alt="image" src="https://github.com/user-attachments/assets/99723c95-3371-4a73-8f61-486e0f97676c" />
</div>

## Synthesizing mult8

<div align="center">
   <img width="855" height="556" alt="image" src="https://github.com/user-attachments/assets/5207ba11-76c1-4a3e-994f-b549c9c45ce0" />
</div>




