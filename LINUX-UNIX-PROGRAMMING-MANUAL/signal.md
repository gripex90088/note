### 信号

> 信号是事件发生时对进程的通知机制， 有时也称为软中断

> 针对每个信号，都定义了一个唯一的(小)整数，从1开始顺序展开。<signal.h>以SIGXXX形式的符号名对这些整数做了定义。



+ 信号分为两大类
  1. 第一组用于内核向进程通知事件(传统信号或标准信号)，Linux中标准信号的编号为1-31
  2. 实时信号（22.8节)

，