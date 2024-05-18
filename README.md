# EXPERIMENT-4 SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS
# DATE:
# AIM:
To simulate and synthesis SR, JK, T, D - FLIPFLOPS, COUNTERS design using vivado.

# APPARATUS REQUIRED:
vivado 2023.2

# PROCEDURE
STEP:1 Start the vivado software, Select and Name the New project.

STEP:2 Select the device family, device, package and speed.

STEP:3 Select new source in the New Project and select Verilog Module as the Source type.

STEP:4 Type the File Name and module name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the run simulation and then run Behavioral Simulation in the Source Window and click the check syntax.

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

STEP:7 compare the output with truth table.

# LOGIC DIAGRAM
# SR FLIPFLOP
![image](https://github.com/Irakamchaitanya/VLSI-LAB-EXP-4/assets/161814091/1996a5b7-36b2-4b60-a862-12238cedff82)


# JK FLIPFLOP
![image](https://github.com/Irakamchaitanya/VLSI-LAB-EXP-4/assets/161814091/6351f0ff-e7a0-45b2-91a7-17d36e9da531)


# T FLIPFLOP
![image](https://github.com/Irakamchaitanya/VLSI-LAB-EXP-4/assets/161814091/e55a85f0-e43a-430b-bfa2-6ed68fcf6703)


# D FLIPFLOP
![image](https://github.com/Irakamchaitanya/VLSI-LAB-EXP-4/assets/161814091/1f788438-9fff-4c9c-8cd7-25d6df1310e6)


# COUNTER
![image](https://github.com/Irakamchaitanya/VLSI-LAB-EXP-4/assets/161814091/f53bc6c4-0d1d-4b22-a3e9-ea3fbcdfecf2)


# VERILOG CODE
# SR FLIPFLOP:
module srff(clk,j,k,rst,q );

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

endmodule

# JK FLIPFLOP:
module jkff(clk,j,k,rst,q );

input j,k,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

begin

case({j,k})

2'b00: q=q;

2'b01:q=1'b0;

2'b10:q=1'b1;

2'b11:q=~q;

endcase

end

end

endmodule

# T FLIPFLOP:
module tff(clk,reset,t,q);

input clk,reset,t;

output reg q;

always @(posedge clk)

begin

if(reset==1)

q=0;

else

begin

if(t==0)

q=q;

else

q=~q;

end

end

endmodule

# D FLIPFLOP:
module dff(clk,d,rst,q );

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

# UPDOWN COUNTER:
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

# MOD 10 COUNTER:
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

# RIPPLE COUNTER:
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

# OUTPUT WAVEFORM
# SR flipflop:
![image](https://github.com/Irakamchaitanya/VLSI-LAB-EXP-4/assets/161814091/7521d1d6-11d8-434f-b3a3-1d2500f90e29)

# JK flipflop:
![image](https://github.com/Irakamchaitanya/VLSI-LAB-EXP-4/assets/161814091/10fc2d35-f4f7-4856-822f-a7ef244a2e3f)

# T flipflop:
![image](https://github.com/Irakamchaitanya/VLSI-LAB-EXP-4/assets/161814091/f88b8655-2d45-4200-9d71-f348d236ef03)

# D flipflop:
![image](https://github.com/Irakamchaitanya/VLSI-LAB-EXP-4/assets/161814091/3d253b72-9254-4cb8-96cf-4a7a42404c3a)

# Updown counter:
![image](https://github.com/Irakamchaitanya/VLSI-LAB-EXP-4/assets/161814091/c27ff1b3-c0c3-4556-b0fd-7226f603f988)

# Mod 10 counter:
![image](https://github.com/Irakamchaitanya/VLSI-LAB-EXP-4/assets/161814091/8a037f14-d3f2-470e-90d4-ffc2e1823ce1)

# Ripple counter:
![image](https://github.com/Irakamchaitanya/VLSI-LAB-EXP-4/assets/161814091/67cc266b-91f0-4b00-aee6-c1405bb3d8cb)


# RESULT
Thus,the simulation and synthesis of SR,JK,T,D flipflops,counters by using vivado has been successfully excecuted and verified.
