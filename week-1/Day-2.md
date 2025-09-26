# Day 2: Timing libs, Hierarchial Vs Flat Synthesis and Efficient Flop Coding Styles
# 1. Introduction to timing.libs
## 👉🏼 Technology Library Analysis
*Go to library directory*
```bash
cd vlsi/sky130RTLDesignAndSynthesisWorkshop/lib
```
*Open Libaray Files*
```bash
nano sky130_fd_sc_hd__tt_025C_1v80.lib
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/0a1be705-8101-463a-be0f-6bf6ca5b1649" />

*To find cells*
```bash
ctrl+W -> write name of the cells
```
<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/bbaaba66-25bd-4bb4-baaa-77eee266a0b3" />

# 2. Hierarchial Vs Flat Synthesis
| Hierarchial | Flat Synthesis |
|----------|----------|
| Design is partitioned into modules/blocks.    | Entire design is synthesized as one single block.     | 
|Faster compile time for large designs    | Longer compile/runtime, especially for large designs.     | 
|Easier debugging & reuse of modules. | Harder to debug or reuse specific modules. |

## 👉🏼  Hierarchial Synthesis 
*Go to Directory*
```bash
cd vlsi/sky130RTLDesignAndSynthesisWorkshop/verilog_files
```
*Invoke Yosys*
```bash
yosys
```
*Read Libarary and Verilog Files*
```bash
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog multiple_modules.v
```
```bash
synth -top multiple_modules
```
<img width="655" height="524" alt="image" src="https://github.com/user-attachments/assets/c2127a0c-a00c-43b4-9426-4628fa4d64d7" />
<img width="655" height="524" alt="image" src="https://github.com/user-attachments/assets/35439727-5287-4d7d-9a1c-9f20cc028f96" />

*Convert RTL file to Gate level*
```bash
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
*Graphical Layout (Schematic Output)*
```bash
show -format png  multiple_modules
```
<img width="694" height="157" alt="image" src="https://github.com/user-attachments/assets/e53e4569-157e-46b1-9063-d46156b35c6e" />

*Write Netlist File*
```bash
write_verilog -noattr multiple_modules_hier_netlist.v
```
<img width="694" height="534" alt="image" src="https://github.com/user-attachments/assets/7f37f70c-e19c-47b7-a0de-3263b2221891" />

## 👉🏼 Flat Synthesis
*Again Invoke yosys and follow same process till gate level*
```bash
flatten
```
*Graphical Layout (Schematic Output)*
```bash
show -format png  multiple_modules
```
*Write Netlist File*
```bash
write_verilog -noattr multiple_modules_flat.v
```

# 3. Various Flop Coding Styles and Optimization
## 👉🏼 Asynchronous Flip Flop
Reset/Set can happen **immediately, independent of clock.**
*Go to Directroy*
```bash
```
```bash
iverilog dff_asyncres.v tb_dff_asyncres.v
./a.out
```
```bash
gtkwave  ./tb_dff_asyncres.vcd
```
*Next is Asynchronous Set*
```bash
iverilog dff_async_set.v tb_dff_async_set.v
./a.out
```
```bash
gtkwave  ./tb_dff_async_set.vcd
```

## 👉🏼 Synchronous Flip Flop
```bash
iverilog dff_syncres.v tb_dff_syncres.v
./a.out
```
```bash
gtkwave  ./tb_dff_syncres.vcd
```
