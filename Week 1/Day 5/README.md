# Optimization in Synthesis
## What is Synthesis Optimization
When you synthesize RTL to a netlist of gates, the initial netlist may not be efficient.
- Optimization improves by
    - Reducing area
    - Increasing speed
    - Reducing the power

## If Case Constructs
If-else statemnts are used for conditional execution

## Lab on In-complete if
## incomp_if.v
<div align="center">
  <img width="700" height="200" alt="image" src="https://github.com/user-attachments/assets/8a2eec3f-b74d-4ede-ab2e-0479c75f6f8e" />
  <img width="700" height="106" alt="image" src="https://github.com/user-attachments/assets/869a9e8e-085c-484d-93bc-14608a869844" />
  <img width="700" height="390" alt="image" src="https://github.com/user-attachments/assets/4f0bfbf3-7f37-45d8-b851-846020899388" />
  <img width="700" height="144" alt="image" src="https://github.com/user-attachments/assets/03d38f66-602f-428c-8352-a3ab3dd67086" />
  <img width="700" height="500" alt="image" src="https://github.com/user-attachments/assets/81c3efa9-3fd1-421c-bba6-62e7a439db85" />
</div>

## incomp_if2.v
<div align="center">
  <img width="700" height="254" alt="image" src="https://github.com/user-attachments/assets/2693d20b-ff0f-46ba-8549-12200ad2dcf9" />
  <img width="700" height="90" alt="image" src="https://github.com/user-attachments/assets/75228abe-addc-42d7-8624-f22f6db8589c" />
  <img width="700" height="416" alt="image" src="https://github.com/user-attachments/assets/e897c2c9-013c-41e6-8e61-f785cbfe0414" />
  <img width="700" height="500" alt="image" src="https://github.com/user-attachments/assets/7e00c2dd-37ac-466b-8028-89c7f87ecfdd" />
</div>

## incomp_case.v
<div align="center">
  <img width="700" height="200" alt="image" src="https://github.com/user-attachments/assets/ad26946f-8e93-4772-9776-2fa844c1a5c0" />
  <img width="700" height="90" alt="image" src="https://github.com/user-attachments/assets/9607f7f6-cd3d-40b9-aac5-ece54689264c" />
   <img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/5be62017-4230-4b90-a11b-79c030914198" />
  <img width="700" height="188" alt="image" src="https://github.com/user-attachments/assets/b115a3ed-81f5-4f43-a2ff-de72a23dfd4c" />
  <img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/cd58f56b-3eef-4e98-aa10-1c2192e4b2ea" />
  <img width="700" height="285" alt="image" src="https://github.com/user-attachments/assets/79c89807-c168-4ca1-823c-3d034848ee0b" />
</div>

## comp_case.v
<div align="center">
  <img width="700" height="199" alt="image" src="https://github.com/user-attachments/assets/757d25da-ff3b-4022-bcdf-5c8990d6d0a8" />
  <img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/87fc7738-cd53-49d2-90f3-1e64b2bc9c54" />
  <img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/24a8c2ff-0a64-4a21-8c7c-1777ced4f56e" />
  <img width="500" height="180" alt="image" src="https://github.com/user-attachments/assets/3948d293-4efe-4917-a73b-b7517ae72408" />
  <img width="700" height="300" alt="image" src="https://github.com/user-attachments/assets/58279f1b-4dbc-46d1-9ab3-abaf85d929a7" />
</div>

## bad_case.v
<div align="center">
   <img width="700" height="200" alt="image" src="https://github.com/user-attachments/assets/396a9e8c-7f89-4e6b-b350-1476b63d6c78" />
   <img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/ace00ead-e020-4d0b-b4ac-104c07660d1c" />
</div>

## partial_case_assign.v
<div align="center">
   <img width="700" height="322" alt="image" src="https://github.com/user-attachments/assets/4f7a2f1e-47a2-4d2d-909f-0ca7565b0b5c" />
   <img width="400" height="500" alt="image" src="https://github.com/user-attachments/assets/b8fcadc1-4d03-491f-ba6f-a9e5a23cf313" />
   <img width="500" height="188" alt="image" src="https://github.com/user-attachments/assets/66c6b7e1-2a77-46f6-8a82-ae97205563ab" />
   <img width="700" height="300" alt="image" src="https://github.com/user-attachments/assets/2e1244d5-dacc-4d00-bc25-1e9dbda968bb" />
</div>

## Looping Constructs
There are 2 looping constructs
- for loop
- for generate

## for loop
- Used inside procedural blocks (always, initial)
- Purpose: repeated operations on arrays, buses or signals
- Simulation: executes sequentially
- Used for evaluating expressions
- Not for instantiating hardware

## for generate
- Used outside procedural blocks
- Purpose: replicate hardware instances (modules, wires, regs, logic)
- Instantiating a hardware multiple times
    
## Lab for mux_grnerate.v
<div align="center">
   <img width="665" height="290" alt="image" src="https://github.com/user-attachments/assets/87dbdfbb-ccaa-4ff6-a5ac-64942b5e642e" />
   <img width="896" height="477" alt="image" src="https://github.com/user-attachments/assets/65c3d012-23ee-4ba7-9dd6-2b83000854ec" />
</div>

## Lab for demux_case.v
<div align="center">
    <img width="638" height="355" alt="image" src="https://github.com/user-attachments/assets/bb6e27b1-4f89-402a-be0b-189659fcdfb8" />
    <img width="868" height="479" alt="image" src="https://github.com/user-attachments/assets/7265558b-0e0a-4ce8-a579-42ea91fbec98" />
</div>



