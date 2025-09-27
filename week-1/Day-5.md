# Day 5: Optimization in Synthesis

# 1. IF CASE Constructs
dbjfbj
eg counter , caveat(cases)
# 2. Lab: Incomplete IF 
```bash
iverilog incomp_case.v tb_incomp_case.v
./a.out
gtkwave tb_incomp_case.vcd
```
**Synthesis in Yosys**
```bash
read_verilog incomp_case.v
synth -top incomp_case
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show -format png incomp_case
```

## 👉🏼 Lab: Lab Incomplete IF
```bash
iverilog incomp_if2.v tb_incomp_if2.v
./a.out
gtkwave tb_incomp_if2.vcd
```
**Synthesis in Yosys**
```bash
read_verilog incomp_if2.v
synth -top incomp_if2
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show -format png incomp_if2
```

# 3. Lab: Incomplete Overlapping Case (There is no latches)
## 👉🏼 Lab 1:
```bash
iverilog comp_case.v tb_comp_case.v
./a.out
gtkwave tb_comp_case.vcd
```
**Synthesis in Yosys**
```bash
read_verilog comp_case.v
synth -top comp_case
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show -format png comp_case
```

## 👉🏼 Lab 2:
**Synthesis in Yosys**
```bash
read_verilog partial_case_assign.v
synth -top partial_case_assign
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show -format png partial_case_assign
```

## 👉🏼 Lab 3:
```bash
iverilog bad_case.v tb_bad_case.v
./a.out
gtkwave tb_bad_case.vcd
```
**Synthesis in Yosys**
```bash
read_verilog bad_case.v
synth -top bad_case
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show -format png bad_case
```
