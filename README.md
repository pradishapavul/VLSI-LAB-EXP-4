# EXP.No:4
# DATE:02/04/2024

# SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS

# AIM: 
To simulate and synthesis JK-Flipflop, SR-Flipflop, T-Flipflop, D-Flipflop And counters using Vivado 2023.2

# APPARATUS REQUIRED:

vivado 2023

# PROCEDURE:
1.Open Vivado: Launch Xilinx Vivado software on your computer.

2.Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3.Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4.Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5.Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6.Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7.Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8.Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9.View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.

# LOGIC DAIAGRAM
# SR FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)
CODE
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

OUTPUT
![image](https://github.com/pradishapavul/VLSI-LAB-EXP-4/assets/161276575/4c1e0e45-dab6-4ebd-9358-0324d10c912d)



# JK FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)
CODE
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

OUTPUT
![image](https://github.com/pradishapavul/VLSI-LAB-EXP-4/assets/161276575/cc7270c5-2ddc-483c-86a7-71c6745a92d7)

# T FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)
CODE
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

OUTPUT
![image](https://github.com/pradishapavul/VLSI-LAB-EXP-4/assets/161276575/42239fbc-fc58-4336-9432-eba6b58cf588)


# D FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)
CODE
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
OUTPUT
![image](https://github.com/pradishapavul/VLSI-LAB-EXP-4/assets/161276575/6f6555ec-2702-4d12-a0ee-dc7183feb59c)


# COUNTER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)
CODE
module updown(clk,rst,up_down,count);
input clk,rst,up_down;
output reg[3:0]count;
always@(posedge clk)
begin
if(rst==1)
count <= 4'b0000;
else if (up_down == 1'b1)
count <= count + 1'b1;
else
count <= count-1'b1;
end
endmodule

 OUTPUT
 ![image](https://github.com/pradishapavul/VLSI-LAB-EXP-4/assets/161276575/9ebbf365-39ca-4439-977b-d62edcbaf83d)

# MOD10COUNTER
![image](https://github.com/pradishapavul/VLSI-LAB-EXP-4/assets/161276575/30cc3096-1c72-473a-92a5-e9d49bd058bf)
CODE
module mod(clk,rst,count);
input clk,rst;
output reg[3:0]count;
always @(posedge clk)
begin
if(rst==1 | count==4'b1001)
count <= 4'b0000;
else
count <= count +1;
end
endmodule

OUTPUT
![image](https://github.com/pradishapavul/VLSI-LAB-EXP-4/assets/161276575/fcdb452f-8fff-428e-8e55-b3f0c1188c2c)

# RIPPLECARRYCOUNTER
![image](https://github.com/pradishapavul/VLSI-LAB-EXP-4/assets/161276575/f61381cb-d565-4b53-bdc6-743bb9a5c3c1)
![image](https://github.com/pradishapavul/VLSI-LAB-EXP-4/assets/161276575/b165835b-bb48-4498-b3ef-a4cb365f1095)

CODE
module ripplecounter(clk,rst,q);
input clk,rst;
output [3:0]q;
tff tff1(q[0],clk,rst);
tff tff2(q[1],q[0],rst);
tff tff3(q[2],q[1],rst);
tff tff4(q[3],q[2],rst);
endmodule
module tff(q,clk,rst);
input clk,rst;
output q;
wire d;
dff df1(q,d,clk,rst);
not n1(d,q);
endmodule
module dff(q,d,clk,rst);
input d,clk,rst;
output q;
reg q;
always@(posedge clk or posedge rst)
begin
if(rst)
q=1'b10;
else
q=d;
end
endmodule

OUTPUT
![image](https://github.com/pradishapavul/VLSI-LAB-EXP-4/assets/161276575/6356fd85-9f81-4a0c-ac3d-14f0d95bbdc4)

# RESULT:
Thus,the simulation and synthesis of SR,JK,T,D flipflops,counters by using vivado has been successfully excecuted and verified.
















RESULT


