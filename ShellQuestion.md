提示符号(prompt)

1.$:给一般使用者账号使用

2.#:给 root (管理员)账号使用

所谓的命令行,就是在 shell prompt 与 CR 字符之间所输入的文字

Carriage Return(回车) prompt(提示符号) cursor(游标) hard quote(单引号) soft quote(双引号)

一个标准的命令行(command line)格式为: Command-name Options Argument

从技术细节来看,shell 会依据 IFS(Internal Field Seperator) 将 command line 所输入的文字给拆解为"字段"(word)。

然后再针对特殊字符(meta)先作处理,最后再重组整行 command line 。

IFS 是 shell 预设使用的字段分隔符,可以由一个及多个如按键组成:空格键(White Space),表格键(Tab),回车键(Enter)

IFS 是用来拆解 command line 的每一个词(word),因为 shell command line 是按词来处理的。

凡在 hard quote 中的所有 meta 均被关闭。在 soft quoe 中大部份 meta 都会被关闭,但某些则保留(如 $ )。

\ (反斜线),只有紧接在 escape (跳脱字符)之后的单一 meta 才被关闭。

所谓的变量,就是就是利用一个特定的"名称"(name)来存取一段可以变化的"值"(value)。name=value

在设定变量的时侯,得遵守如下规则:

1.等号左右两边不能使用区隔符号(IFS),也应避免使用 shell 的保留字符(meta charactor)。

2.变量名称不能使用 $ 符号。

3.变量名称的第一个字母不能是数字(number)。

4.变量名称长度不可超过 256 个字母。

5.变量名称及变量值之大小写是有区别的(case sensitive)。

区隔符号( : )可以达到扩充目的

```
A=BCD
A=$A:E
```

{} 将变量名称的范围给明确定义出来

```
A=BCD
A=${A}E
```

在当前 shell 中所定义的变量,均属于"本地变量"(local variable),

经过 export 命令的"输出"处理,才能成为环境变量(environment variable)

```
export A=B
```

取消一个变量,在 bash 中可使用 unset 命令来处理

```
unset A
```

```
$ A=            变量 A 设定为"空值"(null value)
$ unset A    让变量 A 不在存在
```

进程(process)

首先,用户执行的任何程序,都是由父进程(parent process)所产生出来的一个子进程(child process),子进程在结束后,将返回到父进程去。在 Linux 系统中被称为 fork 。

当子进程被产生的时候, 将会从父进程那里获得一定的资源分配、以及继承父进程的环境!

所谓环境变量其实就是会传给进程的变量,这就是区分本地变量(子进程环境)与环境变量(父进程环境))的决定性指标。

环境变量只能从父进程到子进程单向继承。换句话说:在子进程中的环境如何变更,均不会影响父进程的环境。

脚本(shell script)：脚本中的命令则是由另外一个非互动模式的子 shell (sub shell)来执行的。

就是 primary shell 产生 sub shell 的进程,sub shell 再产生 script 中所有命令的进程。

正常来说,当我们执行一个 shell script 时,其实是先产生一个 sub-shell 的子进程,然后 sub-shell 再去产生命令的子进程。

source 就是让 script 在当前 shell 内执行、而不是产生一个 sub-shell 来执行。

由于所有执行结果均于当前 shell 内完成,若 script 的环境有所改变,当然也会改变当前环境了!

命令群组(command group):将多个命令集中处理

( ) 将 command group 置于 sub-shell 去执行,也称 nested sub-shell。

{ } 则是在同一个 shell 内完成,也称为 non-named command group

function用法:可以自行定义许许多多好用的 function再集中写在特定文件中,然后,在其它的 script 中用 source 将它们加载并反复执行。

$( ) 是用来做命令替换(command substitution)的,重组命令行

break 是结束 loop,打断当前的循环

return 是结束 function

exit 是结束 script/shell

continue 强迫进入下一次循环动作

变量替换的特性:先替换, 再重组
