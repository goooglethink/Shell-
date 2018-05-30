#### Linux 信号(Signal)

> 信号 : 是在软件层次上对中断机制的一种模拟，采用异步通信方式给某个进程发送信号，行相应的处理函数。
> 
> Linux系统共定义了64种信号，分为两大类：可靠信号与不可靠信号，前32种信号为不可靠信号，后32种为可靠信号。
> 
> 不可靠信号： 也称为非实时信号，不支持排队，信号可能会丢失, 比如发送多次相同的信号, 进程只能收到一次. 信号值取值区间为1~31；
> 
> 可靠信号： 也称为实时信号，支持排队, 信号不会丢失, 发多少次, 就可以收到多少次. 信号值取值区间为32~64。
> 
> 发送信号一般有两种情况：
> 
> 一种是内核检测到系统事件,比如键盘输入 CTRL+C 会发送 SIGINT 信号。
> 
> 另一种是通过系统调用 kill 命令来向一个进程发送信号。

##### Linux 常见的信号：

| item number | index   | default action | introductions              |
| ----------- | ------- | -------------- | -------------------------- |
| 1           | SIGHUP  | 终止             | 终止进程，挂起                    |
| 2           | SIGINT  | 终止             | 键盘输入中断命令,一般是 CTRL+C        |
| 9           | SIGKILL | 终止             | 立即停止进程，不能捕获，不能忽略           |
| 15          | SIGTERM | 终止             | 终止信号，进程会先关闭正在运行的任务再终止，不能捕捉 |
| 18          | SIGCONT | 可忽略            | 让终止的进程继续执行                 |
| 19          | SIGSTOP | 停止             | 停止进程，不能忽略，不能捕获             |
| 20          | SIGSTP  | 停止             | 停止进程，一般是 CTRL+Z            |

> 进程处理信号：
> 
> 1)忽略信号,对信号不做任何处理,其中有两个信号不能忽略:SIGKILL 及 SIGSTOP。
> 
> 2)捕捉信号。
> 
> 3)执行缺省操作,Linux 对每种信号都规定了默认操作。