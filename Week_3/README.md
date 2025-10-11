This week we discuss about the following topics

- Recap of post-synthesis and GLS         Simulation <a href> Post-synthesis and GLS Simulation </a>
- Fundamentals of OpenSTA
- Installation of OpenSTA 






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


