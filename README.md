**4. SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS**

**AIM:**

 To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Xilinx ISE.
 
**APPARATUS REQUIRED:** 

VIVADO 2023.2

**PROCEDURE:**

1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.

**SR FLIPFLOP:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)

**VERILOG CODE:**

~~~
module srff(s,r,clk,rst,q);
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
~~~

**OUTPUT:**

![SR](https://github.com/Dhinesh0024/VLSI-LAB-EXP-4/assets/160568927/0f6d3c8a-68ed-42c1-950f-97b055ceaf98)


**JK FLIPFLOP:**

### Logic Diagram:
![image](https://github.com/karanpro06/VLSI-LAB-EXP-4/assets/119782103/61ba7f5a-accd-496d-a65b-ebef34301d75)

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)

### Verilog Code:

~~~
module jkff(j,k,clk,rst,q);
input j,k,clk,rst;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=0;
else
begin
case({j,k})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=~q;
endcase
end
end
endmodule
~~~

**OUTPUT:**

![JK](https://github.com/Dhinesh0024/VLSI-LAB-EXP-4/assets/160568927/f10f8a81-e7aa-44f7-a5ee-70f276eeb4ba)

**T FLIPFLOP:**

**LOGIC DIAGRAM:**

![image](https://github.com/karanpro06/VLSI-LAB-EXP-4/assets/119782103/43dc6827-07e1-4e92-8e8a-ecc22ce0d6a3)

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)

**VERILOG CODE:**

~~~
module tff(clk,rst,t,q);
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
~~~

**OUTPUT:**

![TFF](https://github.com/Dhinesh0024/VLSI-LAB-EXP-4/assets/160568927/111a7a8f-4e01-4ac4-90c1-4a1a45d13115)


**D FLIPFLOP:**

**LOGIC DIAGRAM:**

![image](https://github.com/karanpro06/VLSI-LAB-EXP-4/assets/119782103/8e827351-3ef8-4a51-9379-1e3baae4baae)


![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)

**VERILOG CODE:**

~~~
module dff(d,clk,rst,q);
input d,clk,rst;
output reg q;
always @(posedge clk)
begin
if (rst==1)
q=1'b0;
else
q=d;
end
endmodule
~~~

**OUTPUT:**

![DFF](https://github.com/Dhinesh0024/VLSI-LAB-EXP-4/assets/160568927/03c4477f-c15a-4898-9e11-df5f1ff4850a)

**COUNTER:**

**Updown Counter:**

**LOGIC DIAGRAM:**

![image](https://github.com/Dhinesh0024/VLSI-LAB-EXP-4/assets/160568927/dd12585a-157f-4b6f-a0c3-b421bb52434c)


![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)

**VERILOG CODE:**

~~~
module udc(clk,rst,updown,out);
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
~~~

**OUTPUT:**

![Screenshot 2024-04-06 134430](https://github.com/Dhinesh0024/VLSI-LAB-EXP-4/assets/160568927/c37fe928-351f-4e40-bf5a-49491aab4bfc)

**MOD 10 COUNTER:**

**LOGIC DIAGRAM:**

![image](https://github.com/Dhinesh0024/VLSI-LAB-EXP-4/assets/160568927/3a4a4da2-7488-411d-8ea5-2e57c4fd942f)


**VERILOG CODE:**

~~~
module mod10(clk,rst,out);
input clk,rst;
output reg [3:0]out;
always@(posedge clk)
begin
if (rst==1 | out==4'b1001)
out=4'b0000;
else
out=out+1;
end
endmodule
~~~

**OUTPUT:**

![Screenshot 2024-04-06 135522](https://github.com/Dhinesh0024/VLSI-LAB-EXP-4/assets/160568927/c6465024-ee28-4781-ba9a-9bec97dd2c1a)

**RIPPLE CARRY COUNTER:**

**LOGIC DIAGRAM:**

![image](https://github.com/Dhinesh0024/VLSI-LAB-EXP-4/assets/160568927/129b1a22-407f-4f38-adff-b4dbf3595eb7)


![image](https://github.com/Dhinesh0024/VLSI-LAB-EXP-4/assets/160568927/fecad9d3-7f49-4c98-91f4-443803a60e37)



**VERILOG CODE:**

~~~
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
always @(posedge clk or posedge rst)
begin
if (rst)
q=1'b0;
else 
q=d;
end
endmodule

module rcc(clk,rst,q);
input clk,rst;
output [3:0]q;
tff tf1(q[0],clk,rst);
tff tf2(q[1],q[0],rst);
tff tf3(q[2],q[1],rst);
tff tf4(q[3],q[2],rst);
endmodule
~~~

**OUTPUT:**

![Screenshot 2024-04-06 144719](https://github.com/Dhinesh0024/VLSI-LAB-EXP-4/assets/160568927/4a1a2d79-9e4d-4b0a-bda9-64bb19952f67)


**RESULT:**

 Hence SR, JK, T, D - FLIPFLOP, COUNTER DESIGN are simulated and synthesised using Xilinx ISE.


