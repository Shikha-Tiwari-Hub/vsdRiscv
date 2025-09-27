# Day 5: Optimization in Synthesis

# 1. IF CASE Constructs
* Used for conditional execution inside always blocks.
* Typical usage: combinational or sequential logic.\
eg counter , caveat(cases)\
**Syntax:**
 ```bash
always @(a or b or sel) begin
    if (sel == 1'b0)
        y = a;
    else
        y = b;
end
```

# 2 . Lab: Incomplete IF 
```bash
iverilog incomp_case.v tb_incomp_case.v
./a.out
gtkwave tb_incomp_case.vcd
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/36302bb5-d6c6-4cb2-b302-8fb1ff832bdc" />

**Synthesis in Yosys**
```bash
yosys
read_verilog incomp_case.v
synth -top incomp_case
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show -format png incomp_case
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/a8299299-5e27-4e4a-892d-e3cdc9f8be06" />

## 👉🏼 Lab: Lab Incomplete IF
```bash
iverilog incomp_if2.v tb_incomp_if2.v
./a.out
gtkwave tb_incomp_if2.vcd
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/939c96ef-6ab8-40be-afb6-beb08170372b" />

**Synthesis in Yosys**
```bash
yosys
read_verilog incomp_if2.v
synth -top incomp_if2
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show -format png incomp_if2
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/12db60d4-97fb-4c38-9e1c-c24098348031" />

# 3. Lab: Incomplete Overlapping Case (There is no latches)
## 👉🏼 Lab 1:
```bash
iverilog comp_case.v tb_comp_case.v
./a.out
gtkwave tb_comp_case.vcd
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/4e5662a9-d255-4ec8-99a5-9538c5d60f16" />

**Synthesis in Yosys**
```bash
read_verilog comp_case.v
synth -top comp_case
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show -format png comp_case
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/88264df8-c629-4584-8ff8-99f5aa11be89" />

## 👉🏼 Lab 2:
**Synthesis in Yosys**
```bash
read_verilog partial_case_assign.v
synth -top partial_case_assign
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show -format png partial_case_assign
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/07acedd6-2b82-44ac-a71e-9b7010bffeda" />

## 👉🏼 Lab 3:
```bash
iverilog bad_case.v tb_bad_case.v
./a.out
gtkwave tb_bad_case.vcd
```
<img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/19f48b1b-8eed-4f7f-9392-0713ea48f37e" />

**Synthesis in Yosys**
```bash
read_verilog bad_case.v
synth -top bad_case
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show -format png bad_case
write_verilog -noattr bad_case_net.v
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/987759bd-6e58-4971-ab7d-0c266ca17b39" />

**GLS**
```bash
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v bad_case_net.v tb_bad_case.v
./a.out
gtkwave  tb_bad_case.vcd
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/4bda1f2d-6525-4733-87a9-4abae6151e26" />

# 4. For Loop and For Generate

## For Loop: 
**Looping Construct - mux and demux**
The for loop is a generate-time construct used to avoid repetitive code.
Often used in parameterized modules or when instantiating multiple similar logic blocks (like MUXes or DEMUXes).

## For Generate:
The generate block is used to create multiple instances of modules or logic at compile time.
Often combined with for, if, or case statements for parameterized hardware replication.

# 5. Lab: For and For Generate
## 👉🏼 Lab: 1
```bash
iverilog mux_generate.v tb_mux_generate.v
./a.out
gtkwave tb_mux_generate.vcd
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/392c0774-4559-4bd9-bc42-ea47b6c70db3" />

## 👉🏼 Lab: 2
```bash
iverilog demux_case.v tb_demux_case.v
./a.out
gtkwave tb_demux_case.vcd
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/0c7609c7-8e45-4e07-8957-12b46c9223f8" />

*For generate*
```bash
iverilog demux_generate.v tb_demux_generate.v
./a.out
gtkwave tb_demux_generate.vcd
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/bae4c030-6fd6-4e3a-b37d-ce905a68e0a2" />

## 👉🏼 Lab: 3
**All the Standard cells are present in the seperate  file so we have to call standard cells**
**(Like GLS Simulation)**
```bash
iverilog fa.v rca.v tb_rca.v
./a.out
gtkwave tb_rca.vcd
```
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/f691da70-0033-433f-a5db-dfc1acc12ecc" />


<p align="center">
  🔹 End of Lab 🔹
</p>
