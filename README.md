EXP-1

Date:

                     SIMULATION OF LOGIC GATES ,ADDERS AND SUBTRACTORS
                                               
AIM:
To simulate Logic Gates ,Adders and Subtractors using Vivado 2023.2.

APPARATUS REQUIRED:
VIVADO 2023.2


PROCEDURE:

STEP:1 Launch the Vivado 2023.2 software.

STEP:2 Click on “create project ” from the starting page of vivado.

STEP:3 Choose the design entry method:RTL(verilog/VHDL).

STEP:4 Crete design source and give name to it and click finish.

STEP:5 Write the verilog code and check the syntax.

STEP:6 Click “run simulation” in the navigator window and click “Run behavioral simulation”.

STEP:7 Verify the output in the simulation window.

LOGIC GATES LOGIC DIAGRAM:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)

 VERILOG CODE
```
module logicgate (a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;  
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b); 
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
```
OUTPUT WAVEFORM

![331342725-06f72e07-8cb7-4e6d-8e2c-990099b5f11d](https://github.com/Udaychaitanya011/VLSI-LAB-EXP-1/assets/161430397/1dc5e80a-a438-4238-bbad-3dc2c359d995)

HALF ADDER LOGIC DIAGRAM

![331342703-4a0e5e6b-09e9-446e-898e-95cb25188dd9](https://github.com/Udaychaitanya011/VLSI-LAB-EXP-1/assets/161430397/94f7fc2a-9cc1-48c1-a6fe-89f8b169c594)

VERILOG CODE
```
module half_adder(a,b,sum,carry);

input a,b;

output sum,carry;

xor g1(sum,a,b);

and g2(carry,a,b);

endmodule
```
OUTPUT WAVEFORM

![331342650-ce7fff0a-0336-4f26-a50c-30f7546ffa4e](https://github.com/Udaychaitanya011/VLSI-LAB-EXP-1/assets/161430397/cc5977a8-a641-44be-a45c-60d5a1d16fd5)

FULL ADDER LOGIC DIAGRAM

![331342621-6d104c09-f1dc-44c2-9a0b-74dada9d223d](https://github.com/Udaychaitanya011/VLSI-LAB-EXP-1/assets/161430397/d63fd6a8-4ea4-407b-8f52-dd8414660634)

VERILOG CODE
```
module fulladder(a,b,c,sum,carry);

input a,b,c;

output sum,carry;

wire w1,w2,w3;

xor(w1,a,b);

xor(sum,w1,c);

and(w2,w1,c);

and(w3,a,b);

or(carry,w2,w3);

endmodule
```
OUTPUT WAVEFORM

![331342586-47929d84-382f-47fa-ba5d-87f3822fe301](https://github.com/Udaychaitanya011/VLSI-LAB-EXP-1/assets/161430397/942f02d4-7d08-4afc-a387-f7e297d65841)

HALF SUBTRACTOR LOGIC DIAGRAM
![331342566-1fb45309-84f4-4293-931c-f70dde701592](https://github.com/Udaychaitanya011/VLSI-LAB-EXP-1/assets/161430397/7ba69920-2eb4-48ee-ab02-b09250f4422f)


VERILOG CODE
```
module halfsub(a,b,diff,borrow);

input a,b;

output diff,borrow;

xor(diff,a,b);

and(borrow,~a,b);

endmodule
```
OUTPUT WAVE

![331342526-07e60246-60a4-4c39-abad-a7e2435bd9c6](https://github.com/Udaychaitanya011/VLSI-LAB-EXP-1/assets/161430397/9f6d3247-62b7-48b3-bd64-523a62861f32)
FORM


FULL SUBTRACTOR LOGIC DIAGRAM

![331342490-2c64f656-51b7-4201-9f64-226fb3f8ffc2](https://github.com/Udaychaitanya011/VLSI-LAB-EXP-1/assets/161430397/63495b96-7ba7-4303-8433-21482f32d75a)


VERILOG CODE
```
module fs(a,b,bin,d,bout);

input a,b,bin;

output d,bout;

wire w1,w2,w3;

xor(w1,a,b);

xor(d,w1,bin);

and(w2,~a,b);

and(w3,~w1,bin);

or(bout,w3,w2);

endmodule
```
OUTPUT WAVEFORM

![331342451-fdc2ca0a-34ac-4f3c-bbab-3adbc9ca953e](https://github.com/Udaychaitanya011/VLSI-LAB-EXP-1/assets/161430397/8c298efc-9db5-4777-be55-a7e8ac97cc7d)

RIPPLE CARRY ADDER LOGIC DIAGRAM
![331342419-c7b76933-7856-4d3e-95b3-dda1cc9b0438](https://github.com/Udaychaitanya011/VLSI-LAB-EXP-1/assets/161430397/c9ecbcee-ba64-49b3-9b8f-f3eb26a8d323)


VERILOG CODE
```
module fulladder(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor(w1,a,b);
xor(sum,w1,c);
and(w2,w1,c);
and(w3,a,b);
or(carry,w2,w3);
endmodule

module rca_8bit(a,b,cin,s,cout);
input [7:0]a,b;
input cin;
output [7:0]s;
output cout;
wire [7:1]w;
fulladder f1(a[0], b[0], cin, s[0], w[1]);
fulladder f2(a[1], b[1], w[1], s[1], w[2]);
fulladder f3(a[2], b[2], w[2], s[2], w[3]);
fulladder f4(a[3], b[3], w[3], s[3], w[4]);
fulladder f5(a[4], b[4], w[4], s[4], w[5]);
fulladder f6(a[5], b[5], w[5], s[5], w[6]);
fulladder f7(a[6], b[6], w[6], s[6], w[7]);
fulladder f8(a[7], b[7], w[7], s[7], cout);
endmodule
```
OUTPUT WAVEFORM

![331342384-ea074c85-bba4-4a51-9dcc-92bc3c0b8651](https://github.com/Udaychaitanya011/VLSI-LAB-EXP-1/assets/161430397/90430024-8e3b-4c43-95a0-3569f1dc30e2)


RESULT:

       simulation of Logic Gates ,Adders and Subtractors using Vivado 2023.2 is verified.
