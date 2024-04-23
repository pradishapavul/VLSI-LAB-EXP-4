# VLSI-LAB-EXP-4
SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS

# AIM: To simulate and synthesis JK-Flipflop, SR-Flipflop, T-Flipflop, D-Flipflop And counters using Vivado 2023.2

# APPARATUS REQUIRED:

vivado 2023

# PROCEDURE:

STEP:1 Start the vivado software, Select and Name the New project.

STEP:2 Select the device family, device, package and speed.

STEP:3 Select new source in the New Project and select Verilog Module as the Source type.

STEP:4 Type the File Name and module name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the run simulation and then run Behavioral Simulation in the Source Window and click the check syntax.

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

STEP:7 compare the output with truth table.

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


  
# PROCEDURE:
STEP:1 Start the vivado software, Select and Name the New project.

STEP:2 Select the device family, device, package and speed.

STEP:3 Select new source in the New Project and select Verilog Module as the Source type.

STEP:4 Type the File Name and module name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the run simulation and then run Behavioral Simulation in the Source Window and click the check syntax.

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

STEP:7 compare the output with truth table.


# VERILOG CODE
module SR(clk,s,r,rst,q );

input s,r,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

begin

case({s,r})

2'b00: q=q;

2'b01:q=1'b0;

2'b10:q=1'b1;

2'b11:q=1'bx;

endcase

end

end

Endmodule

  
# OUTPUT WAVEFORM
 ![image](https://github.com/pradishapavul/VLSI-LAB-EXP-4/assets/161276575/daef65ff-b205-491e-b078-0a7d119b0af2)

 # JK FLIPFLOP:
 ![image](https://github.com/pradishapavul/VLSI-LAB-EXP-4/assets/161276575/83633377-96e2-4cbe-b041-39b6a281432f)

 VERILOG CODE:
module jk(j,k,clk,rst,Q);

input j,k,clk,rst;

output reg Q;

always @(posedge clk)

begin

if(rst==1)Q=0;

else

begin

case({j,k})

2'b00:Q=Q;

2'b01:Q=0;

2'b10:Q=1;

2'b11:Q=~Q;

endcase

end

end

Endmodule

# Output:
![image](https://github.com/pradishapavul/VLSI-LAB-EXP-4/assets/161276575/1023ecae-4efd-414a-8b85-1af21e7d4e38)

# T FLIPFLOP:
![image](https://github.com/pradishapavul/VLSI-LAB-EXP-4/assets/161276575/31ad6a4b-befa-431c-bd2a-92bf9a677449)

# VERILOG CODE:
module tff(t,clk,rst,Q);

input t,clk,rst;

output reg Q;

always @(posedge clk)

begin

if(rst==1)

Q=1'b0;

else if(t==0)

Q=Q;

else

Q=~Q;

end

Endmodule

# Output:
![image](https://github.com/pradishapavul/VLSI-LAB-EXP-4/assets/161276575/d669aafb-e37e-4cd0-b53b-6c90ffa459df)

# D FLIPFLOP:
![image](https://github.com/pradishapavul/VLSI-LAB-EXP-4/assets/161276575/4ff2d994-ced6-4d19-8b4b-603bb5282509)

# VERILOG CODE:
module dff(d,clk,rst,Q);

input d,clk,rst;

output reg Q;

always @(posedge clk)

begin

if(rst==1)

Q=1'b0;

else

Q=d;

end

Endmodule

# Output:
![image](https://github.com/pradishapavul/VLSI-LAB-EXP-4/assets/161276575/9ed68a8a-8233-4ce2-9c30-6cf245fad26f)

# COUNTER:
![image](https://github.com/pradishapavul/VLSI-LAB-EXP-4/assets/161276575/c6b9305e-025d-48c0-b79e-f06d26279ac9)

# 4bit UPDOWN COUNTER

![updown counter vlsi](https://github.com/nithin2134/VLSI-LAB-EXP-4/assets/160302970/63e24e65-fd36-4605-983f-331967760c5d

# VERILOG CODE:
module updown(clk,rst,updown,out);

input clk,rst,updown;

output reg[3:0]out;

always@(posedge clk)

begin

if(rst==1)

out=4'b0000;

else if(updown==1);

out=out-1;

end

endmodule

# Output:
![image](https://github.com/pradishapavul/VLSI-LAB-EXP-4/assets/161276575/5838c29c-be9b-445e-bdbc-a46a565a72aa)

# MOD 10 COUNER:
![image](https://github.com/pradishapavul/VLSI-LAB-EXP-4/assets/161276575/21f59b8e-648a-4bbb-8f96-cbf5c0eb7b74)

# VERILOG CODE:
module mod(clk,rst,out);

input clk,rst;

output reg[3:0]out;

always @(posedge clk)

begin

if(rst==1 | out==4'b1001)

out=4'b0000;

else

out=out+1;

end

endmodule

# Output:
![image](https://github.com/pradishapavul/VLSI-LAB-EXP-4/assets/161276575/a5741855-ef39-407f-bd50-0a2da8e40467)

# RIPPLE CARRY COUNTER:
![image](https://github.com/pradishapavul/VLSI-LAB-EXP-4/assets/161276575/5bbbae81-a6b6-4312-8f2d-c8d8ceadf702)

VERILOG CODE

module ripple_carry_counter(q, clk, reset);

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

# Output:
![image](https://github.com/pradishapavul/VLSI-LAB-EXP-4/assets/161276575/71f5193f-d0eb-4735-a27e-5c9144308936)

# RESULT:
Thus simulate and synthesis JK-Flipflop, SR-Flipflop, T-Flipflop, D-Flipflop And counters was succesfully executed and verified.
















RESULT


