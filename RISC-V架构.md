# RISC-V 架构



### 指令集架构

指令集架构（Instruction Set Architecture，ISA）是 CPU 的灵魂。指令是指处理器进行操作的最小单元（比如加减乘除操作或者读写存储器数据），而指令集则是一组指令的集合。

指令集架构有时候也被称为“处理器架构”。有了指令集架构，便可以使用不同的处理器硬件实现方案来设计不同性能的处理器。处理器的具体硬件实现方案称为微架构（Microarchitecture），虽然不同的微架构实现可能造成性能与成本的差异，但是，软件无须做任何修改便可以完全运行在任何一款遵循同一指令集架构实现的处理器上。

因此，指令集架构可以理解为一个抽象层。该抽象层构成处理器底层硬件与运行于其上的软件之间的桥梁与接口，也是现在计算机处理器中重要的一个抽象层。



### CISC 与 RISC

指令集架构主要分为复杂指令集（Complex Instruction Set Computer，CISC）和精简指令集（Reduced Instruction Set Computer，RISC），两者的主要区别如下：

- CISC 不仅包含了处理器常用的指令，还包含了许多不常用的特殊指令。其指令数目比较多，所以称为复杂指令集。
- RISC 只包含处理器常用的指令，而对于不常用的操作，则通过执行多条常用指令的方式来达到同样的效果。由于其指令数目比较精简，所以称为精简指令集。



### 模块化指令

RISC-V 的指令集使用模块化的方式进行组织，每一个模块使用一个英文字母来表示。RISC-V 最基本也是唯一强制要求实现的指令集部分是由 `I` 字母表示的基本整数指令子集。使用该整数指令子集，便能够实现完整的软件编译器。其他的指令子集部分均为可选的模块，具有代表性的模块包括 M/A/F/D/C。

RISC-V 的模块化指令集

| 基本指令集     | 指令数 | 描述                                                         |
| -------------- | ------ | ------------------------------------------------------------ |
| `RV32I`        | 47     | 32位地址空间与整数指令，支持32个通用整数寄存器               |
| `RV32E`        | 47     | RV32I 的子集，仅支持 16 个通用整数寄存器                     |
| `RV64I`        | 59     | 64位地址空间与整数指令及一部分32位的整数指令                 |
| `RV128I`       | 71     | 128位地址空间与整数指令及一部分64位和32位的指令              |
| **扩展指令集** |        |                                                              |
| `M`            | 8      | 整数乘法与除法指令                                           |
| `A`            | 11     | 存储器原子（Atomic）操作指令和 Load-Reserved/Store-Conditional 指令 |
| `F`            | 26     | 单精度（32比特）浮点指令                                     |
| `D`            | 26     | 双精度（64比特）浮点指令，必须支持 `F` 扩展指令              |
| `C`            | 46     | 压缩指令，指令长度为16位                                     |



比如 RED-V 上面的 SiFive FE310 就是 RV32IMAC 架构。