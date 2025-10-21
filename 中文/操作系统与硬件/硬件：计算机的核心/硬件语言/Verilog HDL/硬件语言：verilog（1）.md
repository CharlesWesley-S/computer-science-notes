# 硬件语言：verilog（1）
verilog是一种硬件描述语言,这种语言与高级语言，汇编语言不同。
高级语言（如 C、Python）是通过操作变量和控制程序流程来实现功能；

汇编语言则更接近底层，直接控制 CPU 的寄存器、内存地址和指令执行顺序；

硬件描述语言（如 Verilog）关注的不是“程序的执行过程”，而是电路中硬件的逻辑结构和行为特性。

## 体会verilog的描述
![alt text](image.png)
在这个电路中，使用了非门，或门与与门这三个门，那么描述硬件语言作用重点是描述，所以代码是

```verilog
module simple_circuit (A,B,C,D,E);
  output D,E;
  input A,B,C;
  wire w1;// 规定了 output，input，wire分别是什么，ABC是输入，DE是输出，还有w1是一条线

  and G1(w1,A,B);
  not G2(E,C);
  or  G3(D,w1,E);
endmodule
```
`module simple_circuit (A,B,C,D,E);`在这里module是指这个电路，然后呢后面的是名字，接下来就是输入输出的线
规定好了输入输出之后，后面就是描述硬件，在图片中会有and逻辑门，那么是A,B连接起来然后呢输出是w1，这是第一句话，同理not，or也是一个思路，写完后，整个电路已经完成了，所以最后是endmodule来结束整个代码。

这个代码本质上没有任何的逻辑，就是单纯的描述电路中逻辑门是怎么排序的，并且按照顺序写下来就行







