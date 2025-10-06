# 2.1 Introduction to Several Major Number Systems

## 2.1.1 Starting with the Decimal System
What is the decimal system? It may seem unfamiliar, but the term's meaning is quite simple. Simply put, it means adding ten to the tenth place (the unit place is ten, and then adding one to the tens place, so it's 10). This is also the principle behind the numbers we use in our daily lives.

10 = 1 * 10<sup>1</sup>
+ 0 * 10<sup>0</sup>
, the answer is 10. Another example:

768 = 7 * 10<sup>2</sup> + 6 * 10<sup>1</sup> + 8 * 10<sup>0</sup> = 700 + 60 + 8

## 2.1.2 Binary System
Binary is similar to decimal, using 2-to-1. 0001 (this is 1, followed by 2, but in binary, 2 needs to be carried forward) is 0010 in binary. Therefore, according to the principle, there is no 2 in binary.

So how do we convert from binary to decimal? It's very simple. The method is the same as for decimal. Since the principle is 2-to-1, we can mimic the decimal process.

1101=1* 2<sup>3</sup> + 1 * 2<sup>2</sup> + 0 * 2<sup>1</sup> + 1* 2<sup>0</sup>=8+4+0+1=13 So this binary number represents 13

## 2.1.3 Hexadecimal system
Hexadecimal, as the name suggests, is sixteen-digit 1, and this sixteen-digit number is

0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A (10), B (11), C (12), D (13), E (14), F (15) These sixteen...

The same principle applies to converting hexadecimal to decimal. Let's take an example (the key idea is to turn what you don't know into what you know).

(1A4)16 (The sixteen is written below the brackets and is a subscript, referring to the meaning of the hexadecimal system.)

=1*16<sup>2</sup> + 10*16<sup>1</sup> + 4*16<sup>0</sup> = 256+160+16 = 432

# 2.2 Random Conversions
These are the three bases you need to know in computers, and you also need to know how to convert between them.

## 2.2.1 Binary to Decimal
This isn't much to explain in the above article. If you want to practice, try 01010101011. Answer: 683.

## 2.2.2 Decimal to Binary Conversion
This hasn't been mentioned before, but it's crucial. For example, what is the binary representation of 25? There's a method for this as well.

Here, we'll use continuous division.

25/2 = 12…………1

12/2 = 6………………0

6/2 = 3………………0

3/2 = 1………………1

1/2 = 0………………1

Writing from the bottom remainder to the top, the answer is 11001.

80/2 = 40…………0

40/2 = 20…………0

20/2 = 10…………0

10/2 = 5………………0

5/2 = 2………………1

2/2 = 1………………0

1/2 = 0………………1

So the answer is 1010000.

This is how to convert binary to decimal.

## 2.2.3 Hexadecimal to Decimal
This has already been done, so there is no need to elaborate. If you want to try it out more, what is the decimal value of AF259? The answer is 716953.

## 2.2.4 Decimal to Hexadecimal
This is actually very simple. It is the same method as converting binary to decimal. However, we need to change 2 to 16.

First, let's do 32.

32/16 = 2………………0

2/16= 0 …………………2

This is (20)16 (still write from the bottom to the top)

## 2.2.5 Hexadecimal to Binary
This hasn't been covered before, so we'll cover it in detail.

(2A3) 16 to binary. We don't have a clue how to solve this problem, but we know how to convert hexadecimal to decimal and decimal to binary, so that's it. First, we convert hexadecimal to decimal, then use the decimal to convert to binary. Our method is to convert hexadecimal to decimal and then use the decimal to convert to binary.

(2A3) 16 = 2*16**2 + 10*16**1 + 3*16**0 = 512 + 160 + 3 = 675

Then use 675 to convert to binary. This process is a bit lengthy, so I'll skip it. Feel free to try it. The answer is 10101. 00011

This approach uses typical science-based thinking, converting what you don't know into what you know to solve the problem. However, this approach is very complex and rarely used in general conversions.

Usually, 0X2A (0X refers to hexadecimal)

0x (see this, the following digits refer to hexadecimal)

2 --> (four-digit binary) 0010 (which is 2)

A --> (four-digit binary) 1010 (which is 10)
So this binary conversion becomes 00101010.

The first approach is the normal one, converting from hexadecimal to decimal and then decimal to binary. This is a very normal approach, but why is the second approach correct?

(A₃A₂A₁A₀)<sub>16</sub> = A₃ × 16<sup>3</sup> + A₂ × 16<sup>2</sup> + A₁ × 16<sup>1</sup> + A₀ × 16<sup>0</sup>

(A₃A₂A₁A₀)<sub>16</sub>
= A₃ × (2<sup>4</sup>)<sup>3</sup> + A₂ × (2<sup>4</sup>)<sup>2</sup> + A₁ × (2<sup>4</sup>)<sup>1</sup> + A₀ × (2<sup>4</sup>)<sup>0</sup>

Simplified exponent:

= A₃ × 2<sup>12</sup> + A₂ × 2<sup>8</sup> + A₁ × 2<sup>4</sup> + A₀ × 2<sup>0</sup>
So A0's range is 0-4, followed by A1's range from 4-8, and so on.

## 2.2.6 Converting Binary to Hexadecimal
This is the same two-step process as above, just reverse it.