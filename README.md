# 4-BIT-RIPPLE-COUNTER

**AIM:**

To implement  4 Bit Ripple Counter using verilog and validating their functionality using their functional tables

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**4 Bit Ripple Counter**

A binary ripple counter consists of a series connection of complementing flip-flops (T or JK type), with the output of each flip-flop connected to the Clock Pulse input of the next higher-order flip-flop. The flip-flop holding the least significant bit receives the incoming count pulses. The diagram of a 4-bit binary ripple counter is shown in Fig. below.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/cb4b74d4-31ab-4359-95d0-d22e67daba13)

In timing diagram Q0 is changing as soon as the negative edge of clock pulse is encountered, Q1 is changing when negative edge of Q0 is encountered(because Q0 is like clock pulse for second flip flop) and so on.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/a573a7d6-014e-4e54-93e6-e2ac9530960b)

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/85e1958a-2fc1-49bb-9a9f-d58ccbf3663c)

**Procedure**
1.Increment count on each positive edge of the clock.
2.Reset count to zero when it reaches 15.
3.Generate clock signal (clk).
4.Instantiate the RippleCounter module.
5.Conduct functional testing by displaying the count at each clock cycle for 16 cycles.
**PROGRAM**
```
module RippleCounter(
   input wire clk,  // Clock input
   output reg [3:0] count // 4-bit counter output
);

// Counter logic
always @(posedge clk) begin
   if (count == 4'b1111) // Reset when count reaches 15
       count <= 4'b0000;
   else
       count <= count + 1; // Increment count
end

endmodule

// Testbench
module RippleCounter_tb;

// Inputs
reg clk;

// Outputs
wire [3:0] count;

// Instantiate the counter
RippleCounter uut(
   .clk(clk),
   .count(count)
);

// Clock generation
initial begin
   clk = 0;
   forever #5 clk = ~clk; // Toggle clock every 5 time units
end

// Stimulus
initial begin
   // Wait for a few clock cycles
   #10;
   
   // Display header
   $display("Time | Count");
   $display("-----------------");
   
   // Functional table testing
   // Increment count 16 times and display the count
   repeat (16) begin
       #5; // Wait for one clock cycle
       $display("%4d | %b", $time, count);
   end
   
   // End simulation
   $finish;
end

endmodule
```
Program for logic gates and verify its truth table in quartus using Verilog programming.

Developed by: THAMEEZ AHAMED A
RegisteNumber: 24013622


**RTL LOGIC FOR 4 Bit Ripple Counter**
![330489871-a0d3aa3d-b3b0-4ce0-89bb-bfa1a8abde7c](https://github.com/RamkumarGunasekaran/4-BIT-RIPPLE-COUNTER/assets/144870820/9cbf71a5-4809-4437-a99f-24d928634e94)

**TIMING DIGRAMS FOR 4 Bit Ripple Counter**
![330489946-a285f70c-c317-4f6e-be38-eef9ecfa250d](https://github.com/RamkumarGunasekaran/4-BIT-RIPPLE-COUNTER/assets/144870820/3e402c9e-f477-44a3-9f01-cd17df84ba77)

**RESULTS**
Thus the program executed succesfully.
