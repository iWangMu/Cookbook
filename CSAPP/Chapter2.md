##### 2.1

A. 0011,1001,1010,0111,1111,1000

B. 0xC97B

C.1101,0101,1110,0100,1100

D. 0x26E7B5

##### 2.2

| n    | 2^n（十进制） | 2^n（十六进制） |
| :--- | :------------ | :-------------- |
| 9    | 512           | 0x200           |
| 19   | 524288        | 0x80000         |
| 14   | 16384         | 0x4000          |
| 16   | 65536         | 0x10000         |
| 17   | 131072        | 0x20000         |
| 5    | 32            | 0x20            |
| 7    | 128           | 0x80            |

##### 2.3

| 十进制 | 二进制    | 十六进制 |
| :----- | :-------- | :------- |
| 0      | 0000 0000 | 0x00     |
| 167    | 1010 0111 | 0xA7     |
| 62     | 0011 1110 | 0x3E     |
| 188    | 1011 1100 | 0xBC     |
| 55     | 0011 0111 | 0x37     |
| 136    | 1000 1000 | 0x88     |
| 243    | 1111 0011 | 0xF3     |
| 82     | 0101 0010 | 0x52     |
| 172    | 1010 1100 | 0xAC     |
| 231    | 1110 0111 | 0xE7     |

##### 2.4

A. 0x5044

B. 0x4FFC

C. 0x503C + 64 = 0x503C + 0x40 = 0x507C

D. 0xAE

##### 2.5

A. 小端法: 21 				大端法: 87

B. 小端法: 21 43			大端法: 87 65

C. 小端法: 21 43 65	   大端法: 87 65 43

##### 2.6

A. 0x00359141 = 0000 0000 0011 0101 1001 0001 0100 0001

​    0x4A564504 = 0100 1010 0101 0110 0100 0101 0000 0100

B. 0000 0000 001***1 0101 1001 0001 0100 0001***

​     0100 1010 0***101 0110 0100 0101 0000 01***00，21位相匹配。

##### 2.7

> 库函数strlen()不计算终止的空字符

61 62 63 64 65 66 

##### 2.8

| 运算 | 结果       |
| ---- | ---------- |
| a    | [01101001] |
| b    | [01010101] |
| ~a   | [10010110] |
| ~b   | [10101010] |
| a&b  | [01000001] |
| a\|b | [01111101] |
| a^b  | [00111100] |

##### 2.9

A. ~黑色=[1,1,1]=白色，~蓝色=[1,1,0]=黄色，~绿色=[1,0,1]=红紫色，~蓝绿色=[1,0,0]=红色，~红色=[0,1,1]=蓝绿色，~红紫色=[0,1,0]=绿色，~黄色=[0,0,1]=蓝色，~白色=[0,0,0]=黑色

B.蓝色|绿色=[0,0,1]|[0,1,0]=[0,1,1]=蓝绿色

黄色&蓝绿色=[1,1,0]&[0,1,1]=[0,1,0]=绿色

红色^红紫色=[1,0,0]^[1,0,1]=[0,0,1]=蓝色

##### 2.10

| 步骤  | *x                | *y                |
| ----- | ----------------- | ----------------- |
| 初始  | a                 | b                 |
| 第1步 | a                 | a^b               |
| 第2步 | a^(a^b)=(a^a)^b=b | a^b               |
| 第3步 | b                 | b^(a^b)=(b^b)^a=a |

##### 2.11

A. first = k, last = k

B. 因为是在对自身求异或

C. for循环中条件判断`first <= last`改成`first < last`

##### 2.12

A. x&0xFF

B.~x^0xFF 或 x^~0xFF

C.x|0xFF

##### 2.13

> bis(x, y) ==> x|y
>
> bic(x, y) ==> x&~y
>
> x^y = (x&~y)|(~x&y)

```c
int bool_or(int x, int y) {
  int result = bis(x, y);
  return result;
}
int bool_xor(int x, int y) {
  int result = bis(bic(x, y), bic(y, x));
  return result;
}
```

##### 2.14

> x = 0x66, 01100110 ; ~x = 10011001; !x = 0x00
>
> y = 0x39, 00111001 ; ~y = 11000110; !y = 0x00

| 表达式   | 值             | 表达式     | 值   |
| -------- | -------------- | ---------- | ---- |
| x & y    | 0x20(00100000) | x && y     | 0x01 |
| x \| y   | 0x7F(01111111) | x \|\| y   | 0x01 |
| ~x \| ~y | 0xDF(11011111) | !x \|\| !y | 0x00 |
| x & !y   | 0x00(00000000) | x && ~y    | 0x01 |

##### 2.15

> x^y，当x==y时为0，x!=y时为非0。

!(x^y)

##### 2.16

| x        |          | x<<3     |          | x>>2(逻辑) |          | x>>2(算术) |          |
| -------- | -------- | -------- | -------- | ---------- | -------- | ---------- | -------- |
| 十六进制 | 二进制   | 二进制   | 十六进制 | 二进制     | 十六进制 | 二进制     | 十六进制 |
| 0xC3     | 11000011 | 00011000 | 0x18     | 00110000   | 0x30     | 11110000   | 0xF0     |
| 0x75     | 01110101 | 10101000 | 0xA8     | 00011101   | 0x1D     | 00011101   | 0x1D     |
| 0x87     | 10000111 | 00111000 | 0x38     | 00100001   | 0x21     | 11100001   | 0xE1     |
| 0x66     | 01100110 | 00110000 | 0x30     | 00011001   | 0x19     | 00011001   | 0x19     |

##### 2.17

| x, 十六进制 | x, 二进制 | B2U(x)               | B2T(x)              |
| ----------- | --------- | -------------------- | ------------------- |
| 0xE         | [1110]    | 2^3+2^2+2^1 = 14     | -2^3+2^2+2^1 = -2   |
| 0x0         | [0000]    | 0                    | 0                   |
| 0x5         | [0101]    | 2^2+2^0 = 5          | 2^2+2^0 = 5         |
| 0x8         | [1000]    | 2^3 = 8              | -2^3 = -8           |
| 0xD         | [1101]    | 2^3+2^2+2^0 = 13     | -2^3+2^2+2^0=-3     |
| 0xF         | [1111]    | 2^3+2^2+2^1+2^0 = 15 | -2^3+2^2+2^1+2^0=-1 |

##### 2.18

A. 0x02e0=[0000 0010 1111 0000]，正数，十进制：736

B. 0xa8=[1010 1000]，负数，[1 0000 0000] - [1010 1000] = [0101 1000]，十六进制：-0x58，十进制：-88

C. 0x28=[0010 1000]，正数，十进制：40

D. 0xd0=[1101 0000]，负数，[1 0000 0000] - [1101 0000] = [0011 0000]，十六进制：-0x30，十进制：-48

E. 0x78=[0111 1000]，正数，十进制：120

F. 0x0088=[0000 0000 1000 1000]，正数，十进制：136

G. 0x01f8=[0000 0001 1111 1000]，正数，十进制：504

H. 0x00c0=[0000 0000 1100 0000]，正数，十进制：192

I. 0xb8=[1011 1000]，负数，[1 0000 0000] - [1011 1000] = [0100 1000]，十六进制：-48，十进制：-72









