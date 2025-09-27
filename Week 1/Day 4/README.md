# GLS, Synthesis-Simulation Mismatch and Blocking/Mon-Blocking Statements

## Why is gate level simulation necessary
- Ensures RTL functionality is preserved after mapping to gates
- Uses actual gate and interconnect delays (via SDF) to catch setup/hold violations
- verifies circuit stability beyond ideal RTL simulation
- checks proper initialization of flip-flops/registers
- Ensures scan chains and test vectors work as intended 
  
<img width="619" height="292" alt="image" src="https://github.com/user-attachments/assets/481af123-f933-40ab-bd65-e89647b2909f" />

## Lab on GLS and synthesis-simulation Mismatch
## Ternary operator Mux (ternary_operator_mux.v)
<div align="center">
  <img width="800" height="97" alt="image" src="https://github.com/user-attachments/assets/562817a0-429f-4c84-8174-f13e9a629e13" />
  <img width="940" height="414" alt="image" src="https://github.com/user-attachments/assets/60068903-e622-4719-8a51-9a3ba10747f2" />
  <img width="940" height="399" alt="image" src="https://github.com/user-attachments/assets/9f50151d-8721-40c0-a874-72dde79c15d6" />  
  <img width="855" height="159" alt="image" src="https://github.com/user-attachments/assets/3f8765fa-46d6-4ba9-8b4f-416695e13f62" />
  <img width="940" height="542" alt="image" src="https://github.com/user-attachments/assets/09d66ddb-2a4a-49ea-88b1-fc5a9ee3216d" />
  <img width="940" height="489" alt="image" src="https://github.com/user-attachments/assets/5eddadc3-af03-4058-b616-e98681276a97" />
</div>

## Bad Mux (bad_mux.v)
<div align="center">
  <img width="940" height="279" alt="image" src="https://github.com/user-attachments/assets/5440c7f4-f053-40a6-8c55-ea29f944f56f" />
	<img width="940" height="397" alt="image" src="https://github.com/user-attachments/assets/8342733c-db1e-4b4e-a5e8-b310079fa4e5" />
  <img width="940" height="499" alt="image" src="https://github.com/user-attachments/assets/4e3421f8-7b6f-4467-b46f-0623ef611f4b" />
  <img width="909" height="453" alt="image" src="https://github.com/user-attachments/assets/1fa7d9a7-2db9-4b16-aaac-9667c32f05c4" />
  <img width="940" height="519" alt="image" src="https://github.com/user-attachments/assets/278971f1-98cf-4472-a9f0-1e90050f8749" />
</div>

## Lab on Synthesis-Simulation Mismatch for Blocking Statements
## Blocking Caveat (blocking_caveat.v)
<div align="center">
  <img width="940" height="234" alt="image" src="https://github.com/user-attachments/assets/e0736ccf-0e08-4d08-84fc-6e7127c8ab2b" />
	<img width="940" height="409" alt="image" src="https://github.com/user-attachments/assets/6fa4f1a4-8852-4348-a92d-e34ffcebb609" />
  <img width="940" height="501" alt="image" src="https://github.com/user-attachments/assets/cae055f4-943d-4730-86b1-dc72dba831dc" />
  <img width="940" height="402" alt="image" src="https://github.com/user-attachments/assets/f1d5bd74-86fc-41ac-83f6-62cf05f82c90" />
</div>


  








