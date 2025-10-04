# Fundamentals and Functional Modelling Of BabySOC - II

# Table of Contents

- [Objective](#1️⃣-objective)
- [Lab Components](#2️⃣-lab-components)
- [Lab Reference](#3️⃣-lab-reference)
- [Step-by-Step Lab Process](#4️⃣-step-by-step-lab-process)
  1. [Clone the Repository](#2-compile-verilog-code)
  2. [Compile Verilog Code](#3-run-simulation)
  3. [Run Simulation](#3-run-simulation)
  4. [Analyze Waveforms](#4-analyze-waveforms)
  5. [ Multi-Module Interaction](#5-multi-module-interaction)
   
# 1️⃣ Objective
The main goal is to:
* Build a **solid understanding of SoC fundamentals**
* Practice **functional modeling** of BabySoC using simulation tools

# 2️⃣ Lab Components
## Tools Required:
* **Icarus Verilog (iverilog**) - For compiling and simulating Verilog code
* **GTKWave** - For viewing and analyzing simulation waveforms

# 3️⃣ Lab Reference
Based on the **VSDBabySoC** Project available at a specific GitHub repository : [git-hub-link](https://github.com/manili/VSDBabySoC.git)

# 4️⃣ Step-by-Step Lab Process
## 1. Clone the Repository
👉🏼 Get the BabySoC project code from GitHub
```bash
git clone https://github.com/manili/VSDBabySoC.git
cd VSDBabySoC
```
```bash
mkdir -p simulation
```
## 2. Compile Verilog Code
👉🏼 Install Sandpiper for Verilog generation from TL-Verilog: rvmyth is in TL-Verilog
```bash
pip3 install pyyaml click sandpiper-saas
sandpiper-saas -i ./src/module/*.tlv -o rvmyth.v --bestsv --noline -p verilog --outdir ./src/module/
```
<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/25c5ec48-2db4-4219-9b3b-a0c29497bedd" />


👉🏼 Use Icarus Verilog to compile all BabySoC modules\
**The simulation was run using Icarus Verilog, and the waveform was inspected in GTKWave to ensure correct operation.**
```bash
iverilog -o simulation/pre_synth_sim.out -DPRE_SYNTH_SIM src/module/testbench.v -I src/include -I src/module
```
## 3. Run Simulation
Execute the simulation to generate .vcd (Value Change Dump) waveform files
```bash
cd simulation
./pre_synth_sim.out
gtkwave pre_synth_sim.vcd
```
<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/f7ef5db9-273b-4d41-b17a-ec6a0cd3ec48" />

### Core WaveForm Output:
Central processor that executes program instructions and coordinates system functions.\
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/0702aaf5-44fb-40cd-899f-853b9b9749a5" />

### PLL WaveForm Output:
 Generates stable clock signals from a reference frequency.\
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/a1cee09f-607a-40a0-afe4-9e0ed0ca4df6" />

### DAC WaveForm Output:
Converts digital signals to analog voltages or currents.\
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/c6c12d8f-ac6c-469d-a295-32d21064ad1d" />

## 4. Analyze Waveforms
Comprehensive analysis of **VSDBabySoC** digital system simulation using **GTKWave VCD file** (pre_synth_sim.vcd). The system demonstrates complex **digital logic** with **mixed-signal** interfaces.\
Open the .vcd files in GTKWave to examine:
  - **Reset operation** - How the system initializes
  - **Clocking** - Timing and synchronization
  - **Dataflow** - How data moves between different modules
### Technical Details
- **Tool**: GTKWave
- **File**: `pre_synth_sim.vcd`
- **Testbench**: `vsdbabysoc_tb`
- **Time Range**: 0-84,999 ns analyzed
- **Signal Types**: wire (all signals)

## 👉🏼 Complete Signal Analysis
### 1. Clock Domain Signals
**Current State**: High **(CLK = 1)**\
**Frequency**: Regular fast clock (~50% duty cycle)\
**Period**: Appears to be consistent throughout\
**Stability**: No glitches or irregularities visible

### 2. REF Signal (Reference Clock)
**Frequency**: Much slower than CLK\
**Pattern**: Periodic pulses with longer low periods\
**Current State**: Low **(REF = 0)**\
<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/9b263e7c-6e3b-4276-842a-f323b717d9a8" />

### 3. Clock Domain Signals
**Current State**: **CLK = 0** (low)\
**Pattern**: Regular square wave oscillation between 0 and 1\
**Duty Cycle**: Appears to be approximately 50% based on the waveform

### 4. REF Signal (Reference Clock)
**Frequency**: Much slower than CLK\
**Pattern**: Periodic pulses with longer low periods\
**Current State**: Low **(REF = 0)**

<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/7ca5a9ec-1783-481b-8ad5-f8132f319833" />

### 5. Control & Status Signals
**END_CP**: Process/operation completion indicator\
**END_VCO**: Sub-module or state machine completion flag\
**reset**: Global system reset (active low observed)

### 6. Data Interface Signals
**RV_TO_DAC[9:0]**: 10-bit data bus to Digital-to-Analog Converter
**VCO_IN**: Control input to voltage-controlled or programmable module
**VREFH**: Voltage reference for analog/mixed-signal components

### 7. System Behavior Analysis
**Clocking Architecture**
* CLK Domain: High-speed system operations
* REF Domain: Reference timing/synchronization
* Relationship: Independent domains with coordinated interaction

### 8. Reset Sequence
**Observation Period**: Reset already deasserted **(reset = 0)**\
**System State**: Normal operation throughout analysis window\
**Stability**: All signals show stable post-reset behavior

### 9. Data Flow Patterns
**RV_TO_DAC Bus Activity**\
Values Observed: 02D, 011, 037, 042, 00X (hexadecimal)\
Pattern: Sequential/controlled value progression\
Purpose: Likely controlling analog parameters or tuning\
**Control Signal Coordination**\
END_VCO = 1 (consistent) -> Sub-module ready/active\
END_CP = X (variable) -> Process-dependent completion\
VCO_IN = 0 -> Control input at baseline

## 5. Multi-Module Interaction
**Observed Module Types**
1. **Clock Management** (CLK, REF generation/distribution)
2. **Digital Control Logic** (State machines, sequencing)
3. **Mixed-Signal** Interface (DAC control, voltage references)
4. T**iming Coordination** (Completion flags, synchronization)

### Signal Group Relationships
* Timing Group: CLK, REF, END_CP, END_VCO
* Data Group: RV_TO_DAC[9:0], OUT
* Control Group: VCO_IN, VREFH, reset
* Analog Interface: RV_TO_DAC, VCO_IN, VREFH

<p align="center">
  🔹 End of Lab 🔹
</p>
