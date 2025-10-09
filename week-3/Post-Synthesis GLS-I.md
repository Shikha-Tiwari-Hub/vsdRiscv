# Post-Synthesis GLS

# 1️⃣ Introduction
In a digital design flow, **Post-Synthesis Gate-Level Simulation (GLS)** and **Static Timing Analysis (STA)** are essential verification stages performed after the synthesis process.

After writing and functionally verifying a design at the **RTL (Register Transfer Level)**, synthesis converts the RTL code into a **gate-level netlist** that uses standard cells from a technology library. This netlist represents how the design will be implemented physically on silicon.\
**Gate-Level Simulation (GLS)** is used to validate that the synthesized netlist behaves the same as the original RTL design. It ensures there are no functional mismatches introduced during synthesis and verifies the correctness of the design with actual gate delays.

# 2️⃣ Objective
* Perform **Gate-Level Simulation (GLS)** after synthesis of the BabySoC design.
* Verify that the GLS results match the **functional simulation** results from **Week 2**.

# 3️⃣ Step-by-Step execution plan for running the commands manually:
🔹**Step 1 :** Perform Synthesis of BabySoC Design
Use Yosys to generate the synthesized netlist from RTL.
👉🏼Invoke yosys
```bash
yosys
```
👉🏼Load the Liberty Files for Synthesis
```bash
read_liberty -lib src/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_liberty -lib src/lib/avsdpll.lib
read_liberty -lib src/lib/avsddac.lib
```
👉🏼 Read Verilog Files
```bash
read_verilog -I ~/babysoc/VSDBabySoC/src/include ~/babysoc/VSDBabySoC/src/module/rvmyth.v
read_verilog -I ~/babysoc/VSDBabySoC/src/include ~/babysoc/VSDBabySoC/src/module/clk_gate.v
read_verilog ~/babysoc/VSDBabySoC/src/module/vsdbabysoc.v
```


