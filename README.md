# EXPERIMENT-4  SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS

# DATE: 

# AIM: 

 To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Xilinx ISE.
 

# APPARATUS REQUIRED:


vivado 14.7
Spartan6 FPGA


# PROCEDURE:

STEP:1  Start  the vivado navigator, Select and Name the New project.
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
**LOGIC DIAGRAM**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)

SR FLIPFLOP

VERILOG CODE

```

module sr_flipflop(s,r,clk,rst,q);
input s,r,clk,rst;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=0;
else
begin
case({s,r})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=1'bX;
endcase
end
end
endmodule

```
OUT PUT:

![image](https://github.com/Sandeep9347/VLSI-LAB-EXP-4/assets/160619092/efcedc5a-ca5c-4865-8c3a-2dd5783f64d5)



LOGIC DAIGRAM:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)

JK FLIPFLOP:

VERILOG CODE:

```

module JK_flipflop (q, q_bar, j,k, clk,reset);
input j,k,clk, reset;
output reg q;
output q_bar;
always@(posedge clk)
begin
  if(!reset)        
    q <= 0;
  else 
  begin
      case({j,k})
        2'b00: q <= q;    // No change
        2'b01: q <= 1'b0; // reset
        2'b10: q <= 1'b1; // set
        2'b11: q <= ~q; // Toggle
      endcase
  end
end
assign q_bar = ~q;
endmodule

```
OUT PUT:

![image](https://github.com/Sandeep9347/VLSI-LAB-EXP-4/assets/160619092/59089ae2-dda9-4062-bf5a-fee0cd11b1c9)



LOGIC DAIGRAM:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)

T FLIPFLOP

VERILOG CODE:
```
module T_flipflop(clk,rst,t,q);
input clk,rst,t;
output reg q;
always @(posedge clk)
begin
if (rst==1)
q=1'b0;
else if (t==0)
q=q;
else
q=~q;
end
endmodule

```
 OUT PUT:

![image](https://github.com/Sandeep9347/VLSI-LAB-EXP-4/assets/160619092/2c169db2-be81-4186-987b-bba341b7f736)


 LOGIC DAIGRAM:

 ![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)

 
D FLIPFLOP:

VERILOG:
```
module Dflipflop(D,clk,reset,Q);
input D;
input clk;
input reset;
output reg Q;
always @(posedge clk)
begin
 if(reset==1'b1)
  Q <= 1'b0;
 else
  Q <= D;
end
endmodule

```

OUT PUT:

![image](https://github.com/Sandeep9347/VLSI-LAB-EXP-4/assets/160619092/faf33cf1-655b-48d9-9946-b7f9adbc6859)



 LOGIC DAIGRAM:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)

RIPPLE CARRY COUNTER:

VERILOG CODE:

```

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
module T_FF(q, clk, reset);
output q;
input clk, reset;
wire d;
D_FF dff0(q, d, clk, reset);
not n1(d, q); 
endmodule
module ripple_carry_counter(q, clk, reset);
output [3:0] q;
input clk, reset;
T_FF tffo(q[0], clk, reset);
T_FF tff1(q[1], q[0], reset);
T_FF tff2(q[2], q[1], reset);
T_FF tff3(q[3], q[2], reset);
endmodule

```

OUTPUT:

![image](https://github.com/Sandeep9347/VLSI-LAB-EXP-4/assets/160619092/c6a29035-a38b-4230-828a-2efda4f41d68)


MOD 10 Counter:

VERILOG CODE:

```

module counter(
input clk,rst,enable,
output reg [3:0]counter_output
);
always@ (posedge clk)
begin 
if( rst | counter_output==4'b1001)
counter_output <= 4'b0000;
else if(enable)
counter_output <= counter_output + 1;
else
counter_output <= 0;
end
endmodule

```

OUT PUT:

![image](https://github.com/Sandeep9347/VLSI-LAB-EXP-4/assets/160619092/30c2c439-5730-4c89-9951-c3ee2170f35a)

UP Down Counter:

VERILOG CODE:

```
module updown_counter(clk,rst,updown,out);
input clk,rst,updown;
output reg [3:0]out;
always@(posedge clk)
begin
if (rst==1)
out=4'b0000;
else if(updown==1)
out=out+1;
else
out=out-1;
end
endmodule

```

OUT PUT:

![image](https://github.com/Sandeep9347/VLSI-LAB-EXP-4/assets/160619092/a38fa9fd-b445-4453-b102-829209f08212)


RESULT:

Thus the simulation and implementation of sequential logic gates is done and verified.


