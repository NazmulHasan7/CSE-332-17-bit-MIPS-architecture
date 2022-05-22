# CSE-332-17-bit-MIPS-architecture
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

<b>17 bit ALU: </b>
The same 1 bit ALU is used to design a 17 bit ALU, so that it can
execute operations on 17 bit operands and generate a 17 bit output

<b>17 bit  Register File:</b>
I have used a 17 bit register file for storing data that are
used the operations in ALU. So, data will be read from here to execute an
instruction, and data may be stored into register after instructions like load
and R type instructions. The register file has RS, RT and RD that are used to
select source and destination registers while decoding an instruction.

<b>ISA</b>
