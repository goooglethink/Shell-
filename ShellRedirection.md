##### 文件描述符(File Descriptor)

> 文件描述符是一个非负整数,在打开现存文件或新建文件时,内核会返回一个文件描述符,读写文件也需要使用文件描述符来访问文件。

| 文件描述符(FD)                          | FD跟设备(device)关联           | 映射关系                           |
| ---------------------------------- | ------------------------- | ------------------------------ |
| 0 : Standard Input (STDIN)         | 标准输入stdin(0):键盘(keyboard) | /dev/stdin -> /proc/self/fd/0  |
| 1 : Standard Output (STDOUT)       | 标准输出stdout(1):屏幕(monitor) | /dev/stdout -> /proc/self/fd/1 |
| 2 : Standard Error Output (STDERR) | 标准错误stderr(2):屏幕(monitor) | /dev/stderr -> /proc/self/fd/2 |

##### 重定向符号

| 符号  | 描述                 |
| --- | ------------------ |
| >   | 符号左边输出作为右边输入(标准输出) |
| >>  | 符号左边输出追加右边输入       |
| <   | 符号右边输出作为左边输入(标准输入) |
| <<  | 符号右边输出追加左边输入       |
| &   | 重定向绑定符号            |

| 实例                | 说明                                        |
| ----------------- | ----------------------------------------- |
| 1 > file 或 > file | 标准输出stdout                                |
| 2 > file          | 标准错误stderr                                |
| &>file 或 >&file   | &将标准输出和标准输入绑定到一起,重定向 file 文件              |
| \> file 2>&1      | 将标准错误 (stderr) 并进 标准输出 (stdout) 作输出,覆盖到文件 |
| &>>file           | 追加重定向标准输出和标准错误到文件                         |
| >> file 2>&1      | 追加重定向标准输出和标准错误到文件 等价于(&>>word)            |