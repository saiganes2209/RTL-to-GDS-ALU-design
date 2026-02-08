# RTL-to-GDS-ALU-design


RTL simulation of ALU 
![ALU_Result](https://github.com/user-attachments/assets/4c0b0390-ffc8-40aa-98d3-4e8d58b14d7c)

RTL Synthesis :
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
# read design
read_verilog mydesign.v

# elaborate design hierarchy
hierarchy -check -top mytop

# the high-level stuff
proc; opt; fsm; opt; memory; opt

# mapping to internal cell library
techmap; opt

# mapping flip-flops to mycells.lib
dfflibmap -liberty mycells.lib

# mapping logic to mycells.lib
abc -liberty mycells.lib

# cleanup
clean

# write synthesized design
write_verilog synth.v
