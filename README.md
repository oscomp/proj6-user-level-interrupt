# proj6-user-level-interrupt

### 项目描述
在用户态直接响应中断，完成进程间通信将极大提高计算机系统中应用的性能。目前，用户态中断/异常的新硬件机制已经出现在2021年底发布的最新的x86-64 至强可扩展处理器（Sapphire Rapids）上，而且RISC-V也指定了对应的N扩展技术草案，允许用户态程序处理中断，该扩展规定了基本的用户态中断控制寄存器和指令的行为。Linux操作系统已经有对Sapphire Rapids用户态中断机制的内核级支持，相关应用的测试性能提高了1~2个数量级。

在常见的操作系统架构中，用户态包含多个进程、线程、任务等软件实体，这些实体间具有一定的隔离性。我们希望这些实体能够各自独立地处理中断，且相互之间可以发送和接收用户态中断。但仅靠基本的N扩展在通信路径上需要大量的内核软件转发，这样的实现方式效率不高，因此需要一种全新的中断控制器硬件（UINTC），在关键路径上减少或消除内核的参与，最终实现一种高效的用户态实体间通信或同步机制。

我们的主要目标包括
1. 在已有用户态中断的Sapphire Rapids x86-64志强处理器上设计实现支持用户态中断的新型操作系统，提高性能和安全性。
2. 在RISC-V64 处理器上实现支持用户态中断/异常的N扩展规范，。

### 所属赛道

2024全国大学生操作系统比赛的“OS功能挑战”赛道

### 参赛要求

- 以小组为单位参赛，最多三人一个小组，且小组成员是来自同一所高校的本科生或研究生
- 如学生参加了多个项目，参赛学生选择一个自己参加的项目参与评奖
- 请遵循“2024全国大学生操作系统比赛”的章程和技术方案要求



### 项目导师
向勇 github https://github.com/xyongcn email xyong@tsinghua.edu.cn
陈渝 github id: chyyuu email：yuchenATtsinghua.edu.cn
贾越凯 github id：equation314 email: jyk19ATmails.tsinghua.edu.cn
尤予阳 github id: Gallium70 email:  youyy18@mails.tsinghua.edu.cn

### 难度

中高等



### 特征

- 最新x86 Sapphire Rapids处理器
- 兼容 RISC-V Privileged 规范 v1.11 版本，可在此基础上进行功能扩增
- FPGA上实现
- 硬件使用Chisel语言实现
- 用C/Rust进行软件开发



### 文档&代码

- [RISC-V "N"扩展技术草案](http://www.five-embeddev.com/riscv-isa-manual/latest/n.html)
- [鲲筋烤参赛队的2021年OS比赛成果](https://gitlab.eduxiji.net/carbon/project325618-89175)
- 已有的uintc规范设计 ( [https://github.com/TRCYX/rv-n-ext-impl/blob/uipi/docs/src/ch2_9_uipi.md](https://github.com/TRCYX/rv-n-ext-impl/blob/uipi/docs/src/ch2_9_uipi.md) )（也可自行设计新的规范），在FPGA上进行硬件实现，接入labeled-RISC-V-N项目 ( [https://github.com/Gallium70/labeled-RISC-V-N](https://github.com/Gallium70/labeled-RISC-V-N) ) 可联系项目导师获取FPGA开发板远程访问权限


### License

- MIT license



## 预期目标

### 注意：下面的内容是建议内容，不要求必须全部完成。选择本项目的同学也可与导师联系，提出自己的新想法，如导师认可，可加入预期目标


### 第一题：支持RV用户态中断机制的新型操作系统
在有初步N扩展规范的RISC-V CPU (FPGA)的基础上，进一步完成以下目标：
* 在rCore-N或zCore内核中实现uintc的驱动
* 为用户态程序提供配置uintc的系统服务接口
* 通过uintc实现用户态程序间的通信
* 测试新型操作系统与传统操作系统下应用的性能差别

### 第二题：支持Sapphire Rapids（x86-64）用户态中断机制的新型操作系统
在有初步支持Sapphire Rapids（x86-64）用户态中断机制的基础上：
* 进一步支持Sapphire Rapids（x86-64）用户态中断机制
* 改进Linux内核，优化Sapphire Rapids（x86-64）用户态中断机制
* 设计实现新型操作系统
* 测试评价有/无用户态中断机制的情况下应用的性能差别
* 测试新型操作系统与传统操作系统下应用的性能差别

### 第三题：探索用户态中断的应用场景

* 使用用户态中断实现所选操作系统的部分职能，可以探索的方向包括但不限于：
  * 用户态异常处理（如整数指令溢出、浮点异常等）
  * 用户态信号（Signal）处理
  * 用户态特权级支持下的异步垃圾回收机制
  * 用户态中断在计算机安全领域的应用

* 撰写文档分析用户态中断在所选择的 OS 上体现出的设计与性能的优势，总结其对操作系统设计的启发意义
* 鼓励同学们探索用户态中断的更多使用场景

