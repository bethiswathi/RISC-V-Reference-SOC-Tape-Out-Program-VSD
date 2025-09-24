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
  <img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/25d3e970-6d9a-47f9-8527-3de4af01f92f" />
</div>
command to write flat netlist

- flatten 

## Sub-Module Lvel Synthesis
Sub module level synthesis optimizes each module individually balancing performance, area and power within its scope.

### Importance of Sub-module level synthesis
Sub-module level synthesis is necessary because 

- Scalability: large massive designs are too big to synthesize flatty. Breaking them into sub-modules makes them manageable.
- Faster Turn-around: Each block can be synthesized,verified and iterated independently, reducing the compile time.
- Reuse of IPs: Pre synthesized/verified sub-modules( like ALUs,memories,controllers) can be reused across multiple designs.
- Debug & ECO ease: Errors can be fixed at sub-module level without re-running synthesis for the full chip.
- Parallel Processing: Different sub-modules can be synthesized concurrently, improving efficiency.
        
<div align="center">
  <img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/ea91b2c9-ebfb-4c87-a21c-94e7dd3439df" />
  <img width="500" height="200" alt="image" src="https://github.com/user-attachments/assets/65ffd506-bc83-44ea-a6f4-ee12c9a570b2" />
  <img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/b847dc62-07f1-47df-a39e-77cffc3b445e" />
  <img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/f8339686-55d1-4fce-92c1-9ca013fb92cb" />
  <img width="600" height="300" alt="image" src="https://github.com/user-attachments/assets/31a5ecbb-ca32-429d-8edb-d00e9dc0d427" />
</div>


## Various Flop Coding Styles and Optimization

  



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


