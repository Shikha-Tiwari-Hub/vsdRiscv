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
```bash
yosys
```
