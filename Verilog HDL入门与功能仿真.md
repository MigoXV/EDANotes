# Verilog HDL入门与功能仿真

## 硬件描述语言简介

一种以文本形式来描述数字系统硬件的结构和行为的语言。

用它可以表示逻辑电路图、逻辑表达式，复杂数字逻辑系统的逻辑功能。

用HDL编写设计说明文档易于存储和修改，并能被计算机识别和处理.

HDL是高层次自动化设计的起点和基础.目前， IEEE推出两种标准：VHDL和Verilog HDL

### VHDL的起源与发展

略

### Verilog HDL的起源与发展

- VHDL

  - 能力

    - 结构建模
    - 抽象能力强
    - 系统级－算法级－RTL级－逻辑级－门级

  - 数据类型

    - 是一种数据类型性极强的语言。支持用户定义的数据类型

    - 当对象的数据类型不一样时必须用类型转换函数转换

    - 可以使用抽象（比如枚举）类型为系统建模

    - 能利用数据类型检查编程的错误

  - 易学性

    是一种数据类型很强的语言，欠直观。加之同一种电路有多种建模方法，通常需要一定的时间和经验，才能高效的完成设计。
    VHDL根植于ADA，有时简洁，有时冗繁，如行为描述简洁，结构描述冗繁。

  - 效率

    由于数据类型严格，模型必须精确定义和匹配数据类型，这造成了比同等地verilog效率要低。

- Verilog

  - 能力

    - 结构建模
    - 具体物理建模能力强
    - 算法级－RTL级－逻辑级－门级－版图级

  - 数据类型

    - 数据类型简单
    - 只能由语言本身定义，不能由用户定义
    - 适于硬件结构的建模，不适于抽象的硬件行为建模

  - 易学性

    由于Verilog为直接仿真语言，数据类型较简单，语法很直观，故Verilog更易理解和好学。
    Verilog更像C，约有50％的结构来自C，其余部分来自ADA。

  - 效率

    不同位宽的信号可以彼此赋值，较小位数的信号可以从大位数信号中自动截取自己的位号。在综合过程中可以删掉不用的位，这些特点使之简洁，效率较高。

### VHDL语言的新进展

- OO-VHDL
- DE-VHDL

### Verilog HDL语言的新进展

- Verilog-AMS
- **SystemVerilog**

### 

## Verilog HDL程序的基本结构

- 大约100个预定义的关键词
- Verilog HDL程序由模块构成。每个模块的内容都是嵌在关键词module和endmodule两个语句之间。每个模块实现特定的功能。
- 每个模块先要进行端口的定义，并说明输入（input) 、输出（output)和双向（inout)，然后对模块功能进行描述。
- 除了endmodule语句外，每个语句后必须有分号。
- 可以用/* --- */和//…..，对VerilogHDL程序的任何部分做注释。

```verilog
/* Gate-level description of a half adder */
module HalfAdder_GL(A, B, Sum, Carry);
  input  A ,B ;		//输入端口声明
  output  Sum, Carry ;      //输出端口声明

  wire A ,B , Sum ,Carry ; 
  
  xor X1 (Sum, A, B );
  and A1 (Carry, A, B);  
endmodule

/* Dataflow description of a half adder */
module HalfAdder_DF(A, B, Sum, Carry);
  input  A ,B ;	 	 
  output  Sum ,Carry ; 
  wire A ,B，Sum ,Carry ; 
  assign   Sum = A ^ B; 
  assign   Carry = A & B; 
 endmodule

/* Behavioral description of a half adder */
module HalfAdder_BH(A, B, Sum, Carry);
  input  A ,B ;	 	  
  output  Sum ,Carry ; 
  reg Sum ,Carry ;    //声明端口数据类型为寄存器
  always @(A or B)  begin
	Sum = A ^ B;	//用过程赋值语句描述逻辑功能
	Carry = A & B;
  end
endmodule

```



