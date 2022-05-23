# <i>CSE-332-17-bit-MIPS-architecture
    CSE332 Computer System Architecture - 17 bit MIPS architecture
<p align="center">
   NORTH SOUTH UNIVERSITY<br>
   Department of Electrical and Computer Engineering
<p>
<p align="center">
  <img src="https://user-images.githubusercontent.com/63312173/169691760-a83acee4-4afd-424a-a34a-986a9d5e06c6.png">
</p>
<p align="center">
   CSE 332 LAB<br>
   Project Title: 17 Bit MIPS Architecture<br>
 <p>

 # Overview
My task was to design 17 bit datapath in Logisim, which can work on R type
and I type instruction. The operations that I have been given are ADD
(addition), MULT (multiplication), X-nor and nor operations. S0, I the main
objective is to design a logisim circuit that can execute these instructions.
 
 # Design Process
<b>1 bit Arithmetic Logic Unit:</b> As I have given 4 operations (addition,
multiplication, x-nor and nor), I have designed a 1 bit ALU unit first. This ALU
unit can execute all these four operations between two input bits and
generates 1 bit output. The desired output is selected with the help of a 4x1
mux that has a 2 bit selection line, used as operation code

<p align="center">
  <img height="300" width="300" src="https://user-images.githubusercontent.com/63312173/169713429-292ef2ed-b83d-4c7f-8efe-68e7ddcab20e.png">
</p>

<b>Operation code</b><br>
&nbsp; &nbsp; &nbsp; 00 --> Addition<br>
&nbsp; &nbsp; &nbsp; 01 --> Multiplication<br>
&nbsp; &nbsp; &nbsp; 10 --> X-nor<br>
&nbsp; &nbsp; &nbsp; 11 --> Nor<br>

<b>17 bit ALU </b>
The same 1 bit ALU is used to design a 17 bit ALU, so that it can
execute operations on 17 bit operands and generate a 17 bit output

<b>17 bit  Register File </b>
I have used a 17 bit register file for storing data that are
used the operations in ALU. So, data will be read from here to execute an
instruction, and data may be stored into register after instructions like load
and R type instructions. The register file has RS, RT and RD that are used to
select source and destination registers while decoding an instruction.

<p align="center">
  <img height="700" width="500" src="https://user-images.githubusercontent.com/63312173/169713610-d7837e4f-0dde-4f11-bf35-da4de7f6c82a.png">
</p>

<b>ISA </b>My ISA bit is 17 bits. I have divided it into 4 parts<br>
Bits 0-3 are for RD (4 bits),<br>
Bits 4-7 are for RT (4 bits),<br>
Bits 8-11 are for RS (4 bits),<br>
Bit 12-16 are for Opcode (5 bits).<br>

<b> Datapath Design </b> It has five stages: fetch, decode, execute, memory access and write back. Fetch unit is for fetching instruction with the help of PC.
Instructions are given into the ROM. For every clock pulse, the next
instruction is fetched. A fetched instruction is then decoded and separated
into RS, RT, RD and Opcode. Based on the type of instruction, RS, RT, RD are
connected to the register file (for R type), or RS, RT are connected to register
file (for I type). Based on the data of RS and RT registers, ALU executes
different instructions. It is the execution unit. Generated result can be stored
on the register (for R type), or an effective memory address can be produced
(for I type instruction). It is done in memory access stage. ALU produced
output can be written into register via the write data line.
In the designed datapath, there is no ALU control, and control unit. So, R type
and I type instructions are selected manually.

<p align="center">
  <img height="300" width="600" src="https://user-images.githubusercontent.com/63312173/169713788-39dd6c00-d2ee-412b-a3ad-51551a8e96ae.png">
</p>

# Instruction Description
<b>ADD:</b> It adds two register values and stores the result into destination
register.<br>
Operation: RD = RS + RT<br>
Assembly code: add RD RS RT.<br><br>
<b>MULT:</b> It multiplies two register values and stores the result into the
destination register.<br>
Operation: RD = RS * RT<br>
Assembly code: mult RD RS RT.<br><br>
<b>X-nor:</b> Performs x-nor operation between two register values and stores the
result into destination register.<br>
Operation: RD = RS X-nor RT<br>
Assembly code: x-nor RD RS RT.<br><br>
<b>nor:</b> Performs nor operation between two register values and stores the
result into destination register.<br>
Operation: RD = RS nor RT<br>
Assembly code: nor RD RS RT.<br><br>
<b>Lw:</b> Loads value from an effective memory address write it back to the destination register.<br>
Operation: RD = Memory [RD+immediate]<br>
Assembly code: lw RD RS immediate.<br><br>
<b>Sw:</b> It stores value from register to an effective memory address.<br>
Operation: Memory [RT + immediate] = RS<br>
Assembly code: sw RS RT immediate.<br></i>
