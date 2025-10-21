# Hardware language: Verilog (1)
Verilog is a hardware description language, distinct from high-level languages ​​and assembly languages.
High-level languages ​​(such as C and Python) implement functionality by manipulating variables and controlling program flow.

Assembly languages ​​are more low-level, directly controlling CPU registers, memory addresses, and instruction execution order.

Hardware description languages ​​(such as Verilog) focus not on "program execution" but on the logical structure and behavioral characteristics of the hardware within the circuit.

## Experience the description of Verilog
![alt text](image.png)

In this circuit, three gates are used: NOT gate, OR gate and AND gate. The focus of describing the hardware language is description, so the code is
```verilog
module simple_circuit (A,B,C,D,E);
  output D,E;
  input A,B,C;
  wire w1;// It specifies what output, input, and wire are. ABC is input, DE is output, and w1 is a wire.

  and G1(w1,A,B);
  not G2(E,C);
  or  G3(D,w1,E);
endmodule
```

`module simple_circuit (A,B,C,D,E);` Here, `module` refers to the circuit, followed by its name, and then the input and output lines.
After specifying the inputs and outputs, the hardware description follows. In the image, there's an `and` logic gate, so connecting A and B results in a w1 output. This is the first statement. Similarly, `not` and `or` operate similarly. Once written, the circuit is complete, so `endmodule` concludes the code.

This code doesn't inherently have any logic; it simply describes the order of the logic gates in the circuit, and you simply write them in that order.