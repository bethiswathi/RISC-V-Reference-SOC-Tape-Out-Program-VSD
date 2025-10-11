This week we discuss about the following topics

- Recap of post-synthesis and GLS         Simulation <a href="Part_1/README.md">README.md</a>
- Fundamentals of STA<a href="Part_2/README.md">README.md</a>
- Installation of OpenSTA <a href="Part_3/README.md">README.md </a>






### 🧩Related Tools For STA
| Tool | Type | Description |
|------|------|-------------|
| OpenSTA | Open-Source | Used in OpenRoad for timing analysis |  
| PrimeTime | Synopsys | Industry-standard commercial STA |
| Tempus | Cadence | High Performance STA |


**OpenSTA (Open Static Timing Analyzer)**  is an **open-source static timing ananlysis tool** used in VLSI **digital design flows** ---especially within the **OpenRoad poject**.
- It checks whether your synthesized or placed-and-routed digital circuit **meets timing requirements**, without doing time based simulation.

## 🧩What OpenSTA does?
- Analyzes **all possible timing paths** in a circuit statically
- No need for simulation vectors
- Checks for **setup** and **hold time** violations
- Reports slack, arrival times and required times<br><br>
It is used **after synthesis, placement** and **routing** to verify timing closure.


