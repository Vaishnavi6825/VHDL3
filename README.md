# VHDL3
A Full Adder adds three input bits: A, B, and Cin (carry input) and produces two outputs: Sum and Carry


`Aim:`

To design and implement a Full Adder using three different Verilog modeling styles: Dataflow, Behavioral, and Structural modeling. <br>
The goal is to verify the functionality of the Full Adder by simulating it and capturing the output waveforms. <br>

`Apparatus Required:`

-Xilinx Vivado or any Verilog-compatible IDE for simulation. <br>
-Computer with Verilog HDL installed. <br>

`Code Implementation:`

#Dataflow Model: <br>
In the dataflow model, the Full Adder is designed using logical equations for sum and carry.<br>

module full_adder_dataflow(input a, input b, input cin, output sum, output carry);<br>
  assign sum = a ^ b ^ cin;<br>
  assign carry = (a & b) | (b & cin) | (a & cin);<br>
endmodule<br>

#Behavioral Model: <br>
The behavioral model uses an always block to describe the functionality of the Full Adder.<br>

module full_adder_behavioral(input a, input b, input cin, output reg sum, output reg carry);<br>
  always @(*) begin<br>
    sum = a ^ b ^ cin;<br>
    carry = (a & b) | (b & cin) | (a & cin);<br>
  end<br>
endmodule<br>

#Structural Model: <br>
The structural model describes the Full Adder using basic gates and two Half Adders. <br>
A Full Adder can be constructed using two Half Adders and an OR gate for the final carry.<br>

module full_adder_structural(input a, input b, input cin, output sum, output carry);<br>
  wire s1, c1, c2;<br>
  half_adder_structural HA1 (.a(a), .b(b), .sum(s1), .carry(c1));<br>
  half_adder_structural HA2 (.a(s1), .b(cin), .sum(sum), .carry(c2));<br>
  or(carry, c1, c2);<br>
endmodule<br>

![WhatsApp Image 2024-10-15 at 16 09 53_71e4869d](https://github.com/user-attachments/assets/6a565194-69b3-4956-9083-e6fa8beaf6fc)

`Output Waveform:`

![WhatsApp Image 2024-10-15 at 16 05 14_e417dc9d](https://github.com/user-attachments/assets/ac2a66dc-7df9-4946-8245-20afd0efc3e7)

`Result`:

The Full Adder was successfully designed and implemented using Dataflow, Behavioral, and Structural models in Verilog. <br>
The simulation results show correct functionality for each model, with the Sum and Carry outputs matching the expected truth table values.<br>



