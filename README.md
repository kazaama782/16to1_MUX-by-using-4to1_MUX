# 16to1_MUX-by-using-4to1_MUX
behavioral modelling of 4to1 mux by structural modelling of 16to1 mux to make 16to1 mux

`timescale 1ns / 1ps


module mux4to1(out,in,sel);
input [3:0]in;
input [1:0]sel;
output out;
assign out=in[sel];
endmodule

module mux16to1(out,in,sel);
input [15:0]in;
input [3:0]sel;
output out;
wire [3:0]t;
mux4to1 m0(t[0],in[3:0],sel[1:0]);
mux4to1 m1(t[1],in[7:4],sel[1:0]);
mux4to1 m2(t[2],in[11:8],sel[1:0]);
mux4to1 m3(t[3],in[15:12],sel[1:0]);
mux4to1 m4(out,t,sel[3:2]);
endmodule

