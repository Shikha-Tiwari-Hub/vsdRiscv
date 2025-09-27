# Day 2: Timing libs, Hierarchial Vs Flat Synthesis and Efficient Flop Coding Styles
# 1. Introduction to timing.libs
**Timing libraries** describe the **characteristics of standard cells** in a technology, used for synthesis, simulation, and timing analysis.  
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
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/c2127a0c-a00c-43b4-9426-4628fa4d64d7" />
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/35439727-5287-4d7d-9a1c-9f20cc028f96" />

*Convert RTL file to Gate level*
```bash
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
*Graphical Layout (Schematic Output)*
```bash
show -format png  multiple_modules
```
<img width="500" height="157" alt="image" src="https://github.com/user-attachments/assets/e53e4569-157e-46b1-9063-d46156b35c6e" />

*Write Netlist File*
```bash
write_verilog -noattr multiple_modules_hier_netlist.v
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/7f37f70c-e19c-47b7-a0de-3263b2221891" />

## 👉🏼 Flat Synthesis
*Again Invoke yosys and follow same process till gate level*
```bash
flatten
```
*Graphical Layout (Schematic Output)*
```bash
show -format png  multiple_modules
```
<img width="500" height="118" alt="image" src="https://github.com/user-attachments/assets/28c3b891-bcfc-4c0e-9769-abd388c00f02" />

*Write Netlist File*
```bash
write_verilog -noattr multiple_modules_flat.v
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/f2da5853-9d01-4a53-a175-eb5cec0ce933" />

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
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/05f969ec-4a6c-4aac-9a3d-bfb9b13debae" />

*Next is Asynchronous Set*
```bash
iverilog dff_async_set.v tb_dff_async_set.v
./a.out
```
```bash
gtkwave  ./tb_dff_async_set.vcd
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/010c5800-14d9-4509-a9af-445a8785b4b5" />

## 👩🏽‍💻 Synthesis in Yosys
```bash
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_asyncres.v
synth -top dff_asyncres
```
*we have to point same library cells (only for dffs)*
```bash
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/26f64e0a-d6dc-49ff-8b11-29d17add34e5" />

*Standard Synthesis*
```bash
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
```bash
show -format png  dff_asyncres
```
*Next is Asynchronous Set*
```bash
read_verilog dff_async_set.v
```
*we have to point same library cells (only for dffs)*
```bash
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/276e9a99-d40c-4605-adf3-9533f8c9580e" />

*Standard Synthesis*
```bash
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
```bash
show -format png dff_async_set
```

## 👉🏼 Synchronous Flip Flop
```bash
iverilog dff_syncres.v tb_dff_syncres.v
./a.out
```
```bash
gtkwave  ./tb_dff_syncres.vcd
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/8fe3feb4-7bcd-408d-b568-783207f0a982" />

## 👩🏽‍💻 Synthesis in Yosys
```bash
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_syncres.v
synth -top dff_syncres
```
*we have to point same library cells (only for dffs)*
```bash
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
<img width="500" height="467" alt="image" src="https://github.com/user-attachments/assets/79adcb46-4bac-45c5-8fe6-9dc57cc98de9" />

*Standard Synthesis*
```bash
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
```bash
show -format png dff_syncres
```

##  Interesting Optimisations
```bash
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog mult_2.v
synth -top mult_2
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show -format png mult_2
write_verilog -noattr mul2_net.v
```
**output**\
<img width="392" height="163" alt="image" src="https://github.com/user-attachments/assets/bf3a0968-0b7e-407d-aa60-0700059bb5f7" />

*for another verilog files*
```bash
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog mult_8.v
synth -top mult_8
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show -format png mult_8
write_verilog -noattr mul8_net.v
```
**output**\
<img width="392" height="163" alt="image" src="https://github.com/user-attachments/assets/bf31a865-c072-4676-880c-16eca6404c8a" />


<p align="center">
  🔹 End of Lab 🔹
</p>

