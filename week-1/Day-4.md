# Day 4: GLS, Blocking Vs Non-Blocking and Synthesis-Simulation mismatch

# 1. Introduction GLS, Blocking Vs Non-Blocking and Synthesis-Simulation mismatch
## 👉🏼 GLS Concept and Flow using in verilog
dhhd
## 👉🏼 Synthesis-Simulation Mismatch
fhvfr
## 👉🏼 Blocking and Non-Blocking Statements in Verilog
fjfbjv
## 👉🏼 Caveats with Blocking Statements
dhvf
# 2. Lab:  GLS Synth Sim Mismatch
## 👉🏼 Lab 1: 
```bash
cd vlsi/sky130RTLDesignAndSynthesisWorkshop/verilog_files
iverilog ternary_operator_mux.v tb_ternary_operator_mux.v
./a.out
gtkwave tb_ternary_operator_mux.vcd
```
*Synthesis in Yosys*
```bash
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog ternary_operator_mux.v
synth -top ternary_operator_mux 
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
write_verilog -noattr ternary_operator_mux_net.v
show
```
**GLS**
```bash
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v ternary_operator_mux_net.v tb_ternary_operator_mux_net.v
./a.out
gtkwave  tb_ternary_operator_mux_net.v
```
## 👉🏼 Lab 2: 
*Understand the mismatch behaviour*
```bash
cd vlsi/sky130RTLDesignAndSynthesisWorkshop/verilog_files
iverilog bad_mux.v tb_bad_mux.v
./a.out
gtkwave tb_bad_mux.vcd
```
*Synthesis in Yosys*
```bash
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog bad_mux.v
synth -top bad_mux 
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
write_verilog -noattr bad_mux_net.v
show
```
**GLS**
```bash
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v bad_mux_net.v tb_bad_mux_net.v
./a.out
gtkwave  tb_bad_mux_net.v
```
# 3. Lab: GLS Synth Sim Mismatch blocking statement
```bash
cd vlsi/sky130RTLDesignAndSynthesisWorkshop/verilog_files
iverilog blocking_caveat.v tb_blocking_caveat.v
./a.out
gtkwave tb_blocking_caveat.vcd
```
*Synthesis in Yosys*
```bash
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog blocking_caveat.v
synth -top blocking_caveat
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
write_verilog -noattr blocking_caveat_net.v
show
```
**GLS**
```bash
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v blocking_caveat_net.v tb_blocking_caveat_net.v
./a.out
gtkwave tb_blocking_caveat_net.v
```


<p align="center">
  🔹 End of Lab 🔹
</p>

