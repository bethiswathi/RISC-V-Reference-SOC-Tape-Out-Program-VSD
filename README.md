# RISC-V-Reference-SOC-Tape-Out-Program-VSD

## Tools Installation

### **Oracle Virtual machine link**
https://www.virtualbox.org/wiki/Downloads
<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/7bd19570-d25a-4dfb-92fc-91abad89e48b" />

### **System Requirements**
  - 6GB RAM
  - 50 GB HDD
  - Ubuntu 20.04+
  - 4vCPU

### **Tool Check**

### <ins>**Yosys**</ins>
```bash
$ sudo apt-get update
$ git clone http://github.com/YosysHQ/yosys
$ cd yosys
$ sudo apt install make
$ sudo apt-get install build-essential clangbison flex \
  libreadline-dev gawk tcl-dev libffi-devgit \
  graphviz xdotpkg-config python3 libboost -system-dev \
  libboost -python-dev libboost-filesystem-dev zlib1g-dev
$ make config-gcc
$ git submodule update --init --recursive
$ make
$ sudo make install
```

#### <ins>**Iverilog**</ins>
```bash
$ sudo apt-get update
$ sudo apt-get install iverilog
```

#### <ins>**gtkwave**</ins>
```bash
$ sudo apt-get update
$ sudo apt install gtkwave
```
