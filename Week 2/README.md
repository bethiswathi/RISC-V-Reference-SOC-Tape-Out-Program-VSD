# BabySoC Fundamentals and Functional Modelling

## Problem Statement
This work discusses the different aspects of designing a small, compact and open-source **System-on-Chip** (SoC) based on **RVMYTH** a 
RISC-V based processor. This SoC integrates a **Phase Locked Loop (PLL)** for clock generation and control and a **10-bit Digital-to-Analog-Converter (DAC)** for communicating with outside world. By converting digital signals into analog, this DAC allows BabySoC to communicate with the devices such as television and mobile phones which accepts the analog inputs and whose output is in the form of audio or video. Built with **Sky130 technology**, it serves as a **well-documented educational platform** for learning and experimenting with digital-analog interfacing.  

## What is SoC

### <ins>**Definition**</ins>
A **System-on-Chip (SoC)** is an integrated circuit that combines key computer components-like the CPU, GPU, memory controller and I/O interfaces into a single compact chip, instead of using seperate chips for each function.

### <ins>**Main Components of an SoC**</ins>
- **CPU**: Core unit that runs applications, handles calculations and controls the system
- **GPU**: Manages graphics and parallel processing tasks like gaming, video and animations 
- **Memory**:
     - RAM for temporary data while in use
     - ROM/Flash for permanent storage
- **I/O Interfaces**: Allows connection to external devices (ex:- USB, camera, headphones)
- **DSP**: Processes audio and video signals for tasks like noise reduction
- **Power Management**: Regulates and optimizes power usage
- **Special Features**: May include Wi-Fi, Bluetooth and security modules depending omn SoC's purpose.

### <ins>**Advantages of SoC**</ins>
- **Compact Size**: Enables smaller devices by integrating all components on one chip
- **Low Power Consumption**: Efficient design conserves energy, ideal for mobile and IOT
- **High Performance**: Faster internal communication boosts speed
- **Cost Efficiency**: Fewer parts reduce manufaturing and assembly costs
- **Reliability**: Fewer connections mean lower risk of failure

### <ins>**Applications of SoC**</ins>
- **Mobile Devices**: Smartphones and tablets (Ex:-Snapdragon,Apple A-series)
- **IOT & Wearables**: smart-watches, home automation-devices like smart home sensors for monitoring and wireless connectivity
- **Consumer Electronics**: Found in Smart-Tvs, set-up boxes
- **Embedded Systems**: Used in routers, drones, industrial controllers, cars, Tvs and appliances may also use SoC to manage internal funtions

### <ins>**Examples of SoC's**</ins>
- **Apple A series**: Powers iphones and ipads
- **Qualcomm Snapdragon**: Found in many android phones
- **Samsung Exynos**: Used in samsung devices

### <ins>**Challenges with SoC**</ins>
- **Complex Design**: Difficult to integrate many functions on one chip and requires advanced design skills
- **No Upgradability**: Individual parts can't be replaced or upgraded once an SoC is designed
- **Heat Issues**: Integrating many components in small area can cause overheating
- **High Initial Costs**: Expensive to design and manufacture
- **Hard to Debug**: Troubleshooting is more complex
- **Security Risks**: One flaw can impact the entire system

<img width="803" height="400" alt="image" src="https://github.com/user-attachments/assets/e34a5321-98d2-4a8e-acf1-aaa1a497f372" />

## SoC Design Flow

## Types of SoC
Types of SoCs based on architecture and applications
- **Microcontroller-Based SoC (MCU SoC)**: Combines CPU, memory and basic peripherals for low-power embedded applications, ideal for simple tasks in IOT, appliances and cars. Ex:-STM32, TI MSP430
- **Application-Specific SoC (ASIC SoC)**: Designed for specific high performance tasks graphics, AI or communication. Ex:- Qualcomm, Snapdragon
- **General-Purpose SoC**: Flexible SoC capable of handling various applications typically used in laptops, tablets or servers. Ex:- Apple M-series, AMD embedded SoC

## Introduction to BabySoC
**BabySoC** is a simplified, educational **System-on-Chip (SoC)** platform designed to help students and beginners to understand the basic structure and functionality of an SoC. It's not meant for commercial use but is ideal for learning and experimentation.

## Why BabySoC is ideal for Learning?
- **Simplified design** with only core components
- **Easy to understand** for beginners
- Supports **hands-on-learning** with HDLs and FPGA
- **Customizable** for gradual skill development
- **Low resource needs** accessible for education
- Provides a **safe, controlled environment** for experimentation 

BabySoc provides a hands-on way to
- Understand hardware design principles
- Learn how SoCs integrate processing, memory and I/O
- Practice HDL coding and SoC verification

It serves as a stepping stone to more complex SoC designs by breaking down concepts into manageable parts. 

## Components of BabySoc
- Initialization and Clock Generation using **PLL**: Generates high frequency, stable clock signals from a low-frequency input (eg: crystal oscillator). Initialization begins with Power-on-Reset to set the SoC to a known state.The clock generation process includes **reference clock** as input to PLL. PLL locks to the input frequency and multiplies it to the desired level. Clock is distributed to CPU, memory and peripherals. **Clock gating** is used to disable unused clocks and save power. 
- Data Processing in **RVMYTH**: Acts as data processor using register r17 to hold the values for output. It updagtes r17 in a loop to create a continuous data stream.
- Analog signal generation via **DAC**: The DAC converts these digital values from r17 into an analog signal, saved in a file called OUT. This analog output can be sent to devices like **TVs or phones** to produce **sound or video**, demonstrating real world multimedia interfacing.































