# Assembly Language Basics and Why You Need to Know It
## 1.1 What is Assembly Language and Why Should We Learn It

First, why learn assembly language? This was my biggest confusion when I was learning it. Why learn this abstract subject? Essentially, assembly language helps us gain a deeper understanding of how computers work. Computers appear incredibly "intelligent," capable of performing complex calculations and understanding programs written in high-level languages. But how do they actually do this? Learning assembly language is about exploring these fundamental questions and understanding how computers truly work.

In reality, computers can only understand machine code—binary instructions consisting of strings of 0s and 1s (for example, `010101000...`). However, this format is nearly unreadable to humans (it's all 0s and 1s, making it difficult to understand what they mean). Therefore, assembly language was invented—a mnemonic representation of machine code that makes it easier for humans to write and understand.

Common languages ​​like Java, Python, and C are considered high-level languages. Computers cannot directly understand code written in these high-level languages. Instead, it must be compiled or interpreted, first converted into assembly language or machine code, before being executed by the processor. Ultimately, all program execution returns to the lowest level—through voltage fluctuations and logic gates (such as various combinational logic circuits)—to perform specific operations. Therefore, assembly language serves as a bridge between software and hardware and is essential for understanding computer operations.

## 1.2 ARM Assembly Language and Basic Instructions

### 1.2.1 Introduction to ARM Language

ARM assembly language is a low-level programming language for ARM (Advanced RISC Machine) architecture processors. It adopts the RISC (Reduced Instruction Set Computer) design philosophy, with a concise and efficient instruction set designed to optimize performance and power consumption. ARM assembly language provides direct access to processor registers, memory addresses, and hardware resources, enabling developers to precisely control hardware operations. This language is widely used in embedded systems, mobile devices (such as smartphones and tablets), and IoT devices. Its outstanding performance and low power consumption have made it a mainstream choice in mobile computing. The ARM instruction set includes a variety of instructions, such as data processing, branching, loading, and storing, enabling developers to perform efficient low-level optimizations.

### 1.2.2 Basic Commands
#### 1.2.2.1 MOV Instruction

```arm
MOV R1
```
This instruction initializes a register called r1, which in high-level languages ​​can be understood as creating a variable.

The function of MOV is more complex.

```arm
MOV R1,#3
```
This code is very simple; it simply tells the machine to load the immediate value 3 into R1. This is equivalent to "declaring" and initializing the register. It's very simple. It's exactly the same as in Python:
```python
r1=3
```
(In contrast, variable declaration in Java is more complex, so we won't elaborate on this here.)

```arm
MOV R0, R1
```
This instruction loads r0, which is equal to the value of r1. This isn't exactly the same as r0=r1. In ARM, the value of r1 is placed in r0, so r1 has no value.

In ARM, the value of the subsequent register is moved to the value of the previous register. For example, in the code above, the value of R1 is moved to R0.

This allows us to implement some of our Python code (note that some assembly language logic is different). Its function is to interpret high-level language so that the computer can understand it.

```python
r1 = 5
r2 = 10

# Swap the values ​​of r1 and r2
r1, r2 = r2, r1

print("r1 =", r1)
print("r2 =", r2)

```
This code can be translated using ARM assembly language.

This is the result written in ARM. Let's first explain this code. First, understand what Python code is. In Python, r1 and r2 are swapped. Therefore, the following ARM assembly code should follow the same logic. Note that assembly language logic is very different from high-level language logic; it uses inverse logic.

The ARM logic uses a temporary basket. Apples from basket A are placed in the temporary basket. Bananas from basket B can then be placed in basket A. Finally, the apples from the temporary basket can be placed in basket B, thus achieving a swap. Essentially, ARM also uses this method to access data from two registers.

```arm
MOV R0, #5
MOV R2, #10

MOV R1, R0 @Putting the value of R0 into R1 does not necessarily make R0 and R1 equal. After the value of R0 is placed into R1, R0 is empty. MOV R0,R2 @Since R0 is empty, the value of R2 is moved to R0, completing the process of transferring R2 to R1.
MOV R2,R1 @Finally, the value of R1 (i.e., 5) is moved to R2, completing the conversion.
```

#### 1.2.2.2 Arithmetic Operations

First, addition:

```arm
ADD R0,R0,R1
```
ADD also means addition in English, so in this code, it also means addition. This code first expresses R0 = R0 + R1.

Next, subtraction:
```arm
SUB R0,R0,R1
```
This means R0 = R0 - R1.

Next is multiplication:

```python
MUL R0,R0,R1
```
This means R0 = R0 * R1

Finally, division:

Division is different. If signed (if both variables are positive/zero), UDIV can be used.

```python
UDIV R1,R1,R2
```
This means that if both values ​​are positive/zero (note that R2 is not zero), R1 = R1/R2.

However, if we encounter values ​​with a negative sign, we use SDIV:

```python
SDIV R2,R0,R1
```

This command covers all types of numeric division (including negative, positive, and zero).

Let's take another example.

First, let's look at how Python is written, and then translate this Python code.

```python
x=3
y=3*x**2+2*x+7
print(y)
```
So, how would a computer translate this code? (This Python code simply inserts the value of x into y and then performs the calculation.)


```arm
MOV R0,#3 @x=3

MOV R1,#3 @Coefficient 3
MUL R2,R0,R0 @tmp=x*x
MUL R2,R2,R1 @ R2=3*x**2

MOV R3,#2 @Change coefficient
MUL R4,R0,R3 @R4=2*x

MOV R5,#7 @Constant term

ADD R6, R2,R4 @Add the two
ADD R6,R6,R5 @Don't forget the constant term at the end

```