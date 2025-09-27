# Day 3: Combinational and Sequential Optimizations
# 1. Introduction to Optimization 
Optimization is the process of finding the **best solution** to a problem from a set of possible solutions, usually by **maximizing or minimizing** an objective function (e.g., cost, time, performance, power).

## 👉🏼 Combinational Logic Optimisations
*Go to library directory*
```bash
cd vlsi/sky130RTLDesignAndSynthesisWorkshop/verilog_files
```
*Invoke Yosys*
```bash
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog opt_check.v 
opt_clean -purge
synth -top opt_check
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show -format png opt_check
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/87912cf9-f5c5-461c-baf6-84021879a04e" />

*Therefore we can do same as for other opt_check3*\
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/78548076-969c-4c6a-b2bb-3e97106013a4" />

## 👉🏼 Sequential Logic Optimisations
*Go to library directory*
```bash
cd vlsi/sky130RTLDesignAndSynthesisWorkshop/verilog_files
```
```bash
iverilog dff_const1.v tb_dff_const1.v
./a.out
gtkwave tb_dff_const1.vcd
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/2127792c-a703-40c1-9ad2-f9aa8b922028" />

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
<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/735bf3a2-ecf7-4b74-abe7-9c986da6ad98" />

*Therefore we can do same as for other dff_const2.v,  dff_const3.v* \
**OUTPUT :  dff_const2.v**\
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/dfb759e0-fe53-4303-8b97-3cf7b341e7fd" />
<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/2155ec4e-ee31-413b-b38d-efbf297429c5" />

**OUTPUT :  dff_const2.v**\
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/7e19d649-0216-416d-9cfa-e57797a0bd30" />
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/fcad05e0-9314-4582-9a22-5029a58edd24" />

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
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/b17cacbd-b225-4ac7-98cd-60180c3b391a" />

