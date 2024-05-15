## SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS                                                                                     
## AIM: 
To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Xilinx ISE.

APPARATUS REQUIRED:Xilinx 14.7 Spartan6 FPGA

LOGIC DIAGRAM

SR FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)


JK FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)

T FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)


D FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)


COUNTER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)


  
## PROCEDURE:
STEP:1  Start  the Xilinx navigator, Select and Name the New project.
STEP:2  Select the device family, device, package and speed.       
STEP:3  Select new source in the New Project and select Verilog Module as the Source type.                       
STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.
STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.                       
STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.               
STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.
STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.
STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.

## VERILOG CODE
 SR FLIPFLOP:
```
module srff(s,r,clk,reset,q);
input s,r,clk,reset;
output reg q;
always@(posedge clk)
begin
if(reset==1)
q =1'b0;
else 
begin
case({s,r})
 2'b00: q = q;
 2'b01: q = 1'b0;
 2'b10: q = 1'b1;
 2'b11: q = 1'bx;
 default:q = ~q;
endcase
end 
end
endmodule
```
JK FLIPFLOP:

```
module jk_ff(j,k,clk,reset,q);
input j,k,clk,reset;
output reg q;
always@(posedge clk)
begin
if(reset==1)
q =1'b0;
else 
begin
case({j,k})
 2'b00: q = q;
 2'b01: q = 1'b0;
 2'b10: q = 1'b1;
 2'b11: q = ~q;
 default:q =1'b0;
endcase
end 
end
endmodule
```
T FLIPFLOP:
```
module tff(clk,rst,j,q);
input clk,rst,j;
output reg q;
always@(posedge clk)
begin
case(t)
1'b0:q=q;
1'b1:q=~q;
default=q=1'b0;
endcase
end
endmodule
```
D FLIPFLOP:
```
module dff(clk,rst,d,q);
input clk,rst,d;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=1'b0;
else
q=d;
end
endmodule
```

## OUTPUT WAVEFORM
 SR FLIPFLOP:
![324509227-d67c918e-1436-46fd-a770-5a0ba15f1860](https://github.com/Subash190/VLSI-LAB-EXP-4/assets/162429716/13e1f33c-1adf-4dc3-88d0-5279b36fd951)

JK FLIPFLOP:
![324509302-734000b9-6760-40f3-ab87-74ad84221bbc](https://github.com/Subash190/VLSI-LAB-EXP-4/assets/162429716/76b74f95-caec-4992-8221-175b0c9769ae)


T FLIPFLOP:

![324509374-3bb29062-f124-4ef4-b29b-d4e1441fd7f0](https://github.com/Subash190/VLSI-LAB-EXP-4/assets/162429716/36eeb124-118b-449e-b6dc-a5728784779f)


D FLIPFLOP:

![324509468-71618202-0410-41e9-91b1-bc2ac52d9b3d](https://github.com/Subash190/VLSI-LAB-EXP-4/assets/162429716/29d6adcf-8752-4d13-97bd-b519ee40a844)


## Counter:
## Logic Diagram:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)
## Updown Counter:
## Verilog code:

```
module updowncounter(clk,rst,updown,out);
input clk,rst,updown;
output reg [3:0]out;
always @(posedge clk)
begin
if (rst==1)
out=4'b0000;
else if (updown==1)
out=out+1;
else
out=out-1;
end
endmodule
```
**OUTPUT WAVEFORM:**


![324511432-928169ce-e00f-4ff6-b962-ad94098c6d46](https://github.com/Subash190/VLSI-LAB-EXP-4/assets/162429716/2f263b21-ebe3-4933-86e9-7dd0b55b2af3)

## Mod 10 Counter:
## VERILOG CODE:


```
module mod10counter(clk,rst,out);
input clk,rst;
output reg [3:0]out;
always @(posedge clk)
begin
if (rst==1 | out==4'b1001)
out=4'b0000;
else
out=out+1;
end
endmodule
```

**OUTPUT WAVEFORM:**


![324511702-c7d32766-147b-47be-9c11-847bb388b016](https://github.com/Subash190/VLSI-LAB-EXP-4/assets/162429716/debf0c5e-f52f-4f53-8d76-d85362143882)



## VERILOG CODE:

```
module ripplecounter(q, clk, reset);
output [3:0] q;
input clk, reset;
T_FF tff0(q[0], clk, reset);
T_FF tff1(q[1], q[0], reset);
T_FF tff2(q[2], q[1], reset);
T_FF tff3(q[3], q[2], reset);
endmodule
module T_FF(q, clk, reset);
output q;
input clk, reset;
wire d;
D_FF dff0(q, d, clk, reset);
not n1(d, q); 
endmodule

module D_FF(q, d, clk, reset);
output q;
input d, clk, reset;
reg q;
always @(posedge reset or negedge clk)
if (reset)
q = 1'b0;
else
q = d;
endmodule
```
**OUTPUT WAVEFORM:**

![324510199-da95aafd-b0e6-4ca1-9e0b-70bbd3083e02](https://github.com/Subash190/VLSI-LAB-EXP-4/assets/162429716/a64e330a-45e5-4f46-9246-a498a67cbaec)


**RESULT:**

&emsp;&emsp;Thus the simulation of sequential circuits is done and outputs are verified
successfully.
