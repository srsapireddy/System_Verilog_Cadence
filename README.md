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




