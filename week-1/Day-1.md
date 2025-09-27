# Day 1: Introduction to Verilog RTL design and Synthesis

# 1. Introduction to Open-Source simulator iverilog
- **Icarus Verilog (iverilog)** is an open-source Verilog HDL simulator and compiler.  
- Supports **Verilog-1995/2001/2005** and some **SystemVerilog** features.  
- Works in two steps:  
  1. **Compile** Verilog + Testbench - generates an executable simulation file.  
  2. **Run** the simulation with `vvp` - produces waveforms or console output.  
- Compatible with waveform viewers like **GTKWave** for debugging.  
- Widely used in **academics, research, and open-source VLSI flows** (with Yosys, OpenLane, etc.).  

## 👉🏼 Lab Using iverilog and gtkwave
**1. Introduction to Lab**
```bash
mkdir vlsi
cd vlsi
```
*clone github repo*
```bash
git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/91c57556-c472-4ae6-8d1d-5a6771726141" />

**2. Introduction iverilog and gtkwave**
```bash
cd vlsi/sky130RTLDesignAndSynthesisWorkshop/verilog_files
```
<img width="500" height="228" alt="image" src="https://github.com/user-attachments/assets/19b3b34d-525c-43c8-ae05-644642158bc5" />

*Compile the code*
```bash
iverilog good_mux.v tb_good_mux.v
```
<img width="500" height="119" alt="image" src="https://github.com/user-attachments/assets/e48b5d33-b2ac-4dc9-9e87-737f75909a65" />

*Verify code by using gtkwave*
```bash
gtkwave tb_good_mux.vcd
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/3f755ff7-39ff-40c2-854b-a56e6d5708b6" />

*To see file structure*
```bash
gvim good_mux.v
```

# 2. Introduction to Yosys and Logic Synthesis
- **Yosys** is an open-source framework for **RTL synthesis** of Verilog designs.  
- Converts high-level **RTL code** into a **gate-level netlist** using standard cell libraries.  
- Supports optimization passes like **constant propagation, dead code removal, and technology mapping**.  
- Widely used with tools like **Icarus Verilog (simulation)**, **GTKWave (waveform)**, and **OpenLane (physical design)**.  
- Logic Synthesis flow:  
  1. Parse RTL (Verilog).  
  2. Optimize Boolean logic and finite state machines.  
  3. Map RTL to target **technology library gates**.  
  4. Generate netlist for simulation and backend (P&R).  

## 👉🏼 Lab using Yosys and Sky130 PDKs
**1. Yosys 1  good mux**
*Invoke Yosys*
```bash
cd vlsi/sky130RTLDesignAndSynthesisWorkshop/verilog_files
yosys
```
*Read Libarary and Verilog Files*
```bash
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog good_mux.v
```
<img width="500" height="387" alt="image" src="https://github.com/user-attachments/assets/478c959e-d81b-46cd-bfb7-d6146993c856" />

```bash
synth -top good_mux
```
<img width="500" height="460" alt="image" src="https://github.com/user-attachments/assets/3eb1a129-dcc6-41b4-9751-2f7daa707fed" />

*Convert RTL file to Gate level*
```bash
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
<img width="500" height="444" alt="image" src="https://github.com/user-attachments/assets/e205e9b6-8156-43b5-aa0e-b7beb2e2cc14" />
<img width="500" height="154" alt="image" src="https://github.com/user-attachments/assets/216bc39a-9fbe-4226-ad5f-9308fa74b420" />


*Graphical Layout (Schematic Output)* *this create good_mux.svg in your working directory*
```bash
show -format svg -prefix good_mux
```
<img width="500" height="228" alt="image" src="https://github.com/user-attachments/assets/3ab7ff9a-fa54-4c95-b343-6ffc2501700f" />

*Write Netlist File*
```bash
write_verilog good_mux_netlist.v
write_verilog -noattr good_mux_netlist.v
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/b53bfb0c-6189-4845-81ea-677c6ca9d153" />
<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/97c21b29-df01-4ace-b93d-3d44436a55c9" />


<p align="center">
  🔹 End of Lab 🔹
</p>
