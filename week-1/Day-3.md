# Day 3: Combinational and Sequential Optimizations
# 1. Introduction to Optimization 
Optimization is the process of finding the **best solution** to a problem from a set of possible solutions, usually by **maximizing or minimizing** an objective function (e.g., cost, time, performance, power).

## 👉🏼 Combinational Logic Optimisations
*Go to library directory*
```bash
cd vlsi/sky130RTLDesignAndSynthesisWorkshop/lib
```
*Invoke Yosys*
```bash
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog opt_check.v 
opt_clean -purge
synth -top opt_check
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```
*Therefore we can do same as for other opt_check3*

## 👉🏼 Sequential Logic Optimisations
*Go to library directory*
```bash
cd vlsi/sky130RTLDesignAndSynthesisWorkshop/lib
```
```bash
iverilog dff_const1.v tb_dff_const1.v
./a.out
gtkwave tb_dff_const1.vcd
```
## 👩🏽‍💻 Synthesis in yosys
```bash
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_const1.v
synth -top dff_const1
```
*we have to point same library cells (only for dffs)*
```bash
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
*Standard Synthesis*
```bash
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
*OUTPUT*
```bash
show -format png  dff_const1
```
*Therefore we can do same as for other dff_const2.v,  dff_const3.v* 

## 👉🏼  Sequential Logic Optimisations unused outputs
## 👩🏽‍💻 Synthesis in yosys
```bash
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog counter_opt.v
synth -top counter_opt
```
*we have to point same library cells (only for dffs)*
```bash
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
*Standard Synthesis*
```bash
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
*OUTPUT*
```bash
show -format png counter_opt
```
part3**
