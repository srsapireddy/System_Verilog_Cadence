# System_Verilog_Cadence
## 1.Modeling a Simple Register

![image](https://github.com/srsapireddy/System_Verilog_Cadence/assets/32967087/1d383bf5-0575-42dc-b981-b3edffb7bb0f)

Specification
-	data and out are both 8-bit logic vectors.
-	rst_ is asynchronous and active low.
-	The register is clocked on the rising edge of clk.
-	If enable is high, the input data is passed to the output out.
-	Otherwise, the current value of out is retained in the register.

### Code 
```
module register (
// Verilog2001: port and variable declarations in module definition
// SystemVerilog: logic data type
                output logic [7:0] out,
                input  logic [7:0] data ,
                input        clk  ,
                input        enable  ,
                input        rst_
                );
// SystemVerilog: time unit and time precision declaration
timeunit 1ns;
timeprecision 100ps;

// SystemVerilog: always_ff - sequential behavior intent specification
always_ff @(posedge clk, negedge rst_)
    if (!rst_)
      out <= 0;
    else if (enable)
      out <= data;

endmodule
```

### Output
![image](https://github.com/srsapireddy/System_Verilog_Cadence/assets/32967087/fd6bd253-0b39-4892-a959-bedcde143fc8)

## 2. Modeling a Simple Multiplexor 

![image](https://github.com/srsapireddy/System_Verilog_Cadence/assets/32967087/977c99d6-a0ec-4275-85a6-43781fd03806)

Specification

- in_a, in_b and out are all logic vectors.
- The MUX width is parameterized with a default value of 1.
- If sel_a is 1’b1, input in_a is passed to the output.
- If sel_a is 1’b0, input in_b is passed to the output.

### Code
```
///////////////////////////////////////////////////////////////////////////
//
// File name   : scale_mux.sv
// Title       : MUX Module
// Project     : SystemVerilog Training
// Created     : 2013-4-8
// Description : Defines the mux module
// Notes       :
// Scalable Mux - Specification:
//   when sel_a = 1, out = in_a
//   when sel_a = 0, out = in_b
//   when sel_a = x, out = x
//
///////////////////////////////////////////////////////////////////////////

module scale_mux #(WIDTH = 1)
                  (output logic [WIDTH-1:0] out,
                   input  logic [WIDTH-1:0] in_a,
                   input  logic [WIDTH-1:0] in_b,
                   input  logic sel_a);

timeunit 1ns;
timeprecision 100ps;

always_comb
  unique case (sel_a)
    1'b1: out = in_a;
    1'b0: out = in_b;
    default: out = 'x;
  endcase

endmodule

```
### Output
![image](https://github.com/srsapireddy/System_Verilog_Cadence/assets/32967087/2c06ea95-d283-40a4-8370-5c0f4ce70ad3)




