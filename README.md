# VLSI-LAB-EXP-4
SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS

AIM: 
 To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Xilinx ISE.

APPARATUS REQUIRED:

Xilinx 14.7
Spartan6 FPGA

**LOGIC DIAGRAM**

SR FLIPFLOP

logic diagram

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)

PROGRAM:

module sr_ff(clk,q,rst,s,r);

input s,r,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

begin

case({s,r})

2'b00:q=q;

2'b01:q=1'b0;

2'b10:q=1'b1;

2'b11:q=1'bx;

endcase

end

end

endmodule

output

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/161813818/6d1c77a7-fe36-45e1-9d14-02077462be62)


JK FLIPFLOP

logic diagram

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)

PROGRAM:

module jk_ff(clk,q,rst,j,k);

input j,k,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

begin

case({j,k})

2'b00:q=q;

2'b01:q=1'b0;

2'b10:q=1'b1;

2'b11:q=~q;

endcase

end

end

endmodule

output


![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/161813818/8a43249c-8db2-4b79-8987-a09a39361fd5)


T FLIPFLOP

logic diagram

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)

PROGRAM:

module t_ff(clk,q,rst,t);

input t,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

if(t==0)

q=q;

else

q=~q;

end

endmodule

output


![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/161813818/e3b03480-a136-49e8-a7ba-18a77cbf399c)



D FLIPFLOP

logic diagram

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)

PROGRAM:

module d_ff(clk,q,rst,d);

input d,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

q=d;

end

endmodule

output


![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/161813818/64cae4ab-7753-44d2-8c61-b8a0d6b855f9)



COUNTER

logic diagram

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)


PROGRAM:

module mod_10(clk,rst,out);

input clk,rst;

output reg[3:0]out;

always@(posedge clk)

begin

if(rst==1|out==9)

out=4'b0;

else

out=out+1;

end

endmodule

output


![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/161813818/e05768e1-5214-45eb-9318-12737d25e9e0)



  
PROCEDURE:
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

VERILOG CODE

   <<< TYPE YOUR VERILOG CODE >>>

OUTPUT WAVEFORM
 <<< PASTE YOUR OUTPUT WAVEFORM >>>

RESULT


