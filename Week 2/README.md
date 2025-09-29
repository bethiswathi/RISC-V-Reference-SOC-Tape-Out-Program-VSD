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
- **Apple A17 Pro (iphone)**: Combines CPU, GPU, Neural Engine, ISP and modem
- **Qualcomm Snapdragon 8 Gen 3**: Includes CPU, GPU, AI engine, modem,connectivity features 
- **Rasberry Pi RP2040**: Dual-Core Arm Cortex-MO + CPU with built-in peripherals for embedded applications

  

























