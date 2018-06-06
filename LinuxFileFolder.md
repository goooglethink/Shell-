### Linux 系统常见目录和文件介绍(建议识记)

#### Linux 系统目录结构

| index  | introductions     |
| ------ | ----------------- |
| /      | 根目录,所有文件的第一级目录    |
| /home/ | 普通用户家目录           |
| /root/ | 超级用户家目录           |
| /usr/  | 用户命令、应用程序等目录      |
| /var/  | 应用数据、日志等目录        |
| /lib/  | 库文件和内核模块目录        |
| /etc/  | 系统和软件配置文件         |
| /bin/  | 可执行程序目录           |
| /boot/ | 内核加载所需的文件,grub 引导 |
| /dev/  | 设备文件目录,比如磁盘驱动     |
| /tmp/  | 临时文件目录            |
| /opt/  | 第三方软件安装目录         |

#### Linux 环境变量文件

| index               | introductions                        |
| ------------------- | ------------------------------------ |
| 系统级                 | 系统级变量文件对所有用户生效                       |
| /etc/profile        | 系统范围内的所有环境变量和启动文件，不建议编写该文件           |
| /etc/profile.d/     | 存放自定义的shell脚本目录，便于维护，与/etc/profile等效 |
| /etc/bashrc         | (Red Hat)系统范围内的所有函数和别名               |
| /etc/bash.bashrc    | (Debian)系统范围内的所有函数和别名                |
| 用户级                 | 用户级变量文件对当前用户生效，都在当前用户目录下             |
| $HOME/.bashrc       | 用户指定别名和函数                            |
| $HOME/.zshrc        | 用户指定别名和函数                            |
| $HOME/.bash_logout  | 注销时执行配置文件中的程序                        |
| $HOME/.bash_profile | 用户指定变量和启动程序                          |
| $HOME/.bash_history | 用户执行命令历史文件                           |

> 登录shell时，启动环境变量文件的顺序 : /etc/profile => /etc/profile.d/*.sh => ~/.bash_profile => ~/.bashrc

#### Linux 系统配置文件

| index                           | introductions                            |
| ------------------------------- | ---------------------------------------- |
| /etc/issue                      | 系统版本文件                                   |
| /etc/hosts                      | 主机名与 IP 对应关系文件                           |
| /etc/resolv.conf                | DNS 服务器地址文件                              |
| /etc/hostname                   | 主机名文件                                    |
| /etc/sysctl.conf                | 系统参数配置文件                                 |
| /etc/sudoers                    | sudo 权限配置文件                              |
| /etc/init.d/                    | 服务启动脚本文件夹                                |
| /etc/sysconfig/network-scripts/ | (Red Hat)网卡信息配置文件夹                       |
| /etc/network/interfaces         | (Debian)网卡信息配置文件                         |
| /etc/rc.d/rc.local              | (Cent OS)系统 init 初始化完后执行文件，不建议编写启动服务到该文件 |
| /etc/fstab                      | 硬盘自动挂载配置文件                               |
| /etc/crontab                    | 系统级任务计划文件                                |
| /var/spool/cron                 | 用户级任务计划，此目录下以用户名命名对应每个用户的任务计划            |
| /etc/cron.d/                    | 系统级任务计划目录                                |
| /etc/hosts.allow                | TCP 包访问列表                                |
| /etc/hosts.deny                 | TCP 包拒绝列表                                |
| /usr/share/doc/                 | 系统说明文档和软件帮助文档目录                          |
| /etc/ssh/sshd_config            | OpenSSH服务器端配置文件                          |
| /var/log/                       | 系统和应用程序日志目录                              |
| /var/spool/mail/                | 邮件存放目录                                   |

#### /dev/ 目录 (任何装置与接口设备都会以文件的型态存放在这个目录当中)

| index          | introductions                                           |
| -------------- | ------------------------------------------------------- |
| /dev/hd\[a-t\] | IDE (Integrated Drive Electronics) 电子集成驱动器设备            |
| /dev/sd\[a-z\] | SCSI (Small Computer System Interface) 小型计算机系统接口设备      |
| /dev/dm-\[-9\] | LVM (Logical Volume Manager) 逻辑磁盘                       |
| /**dev**/null  | 空设备，丢弃一切写入其中的数据（但报告写入操作成功），被称为比特桶或者黑洞                   |
| /dev/zero      | 特殊文件，提供无限的空字符(NULL, ASCII NUL, 0x00)，主要用途:提供字符流来初始化数据存储 |

#### /proc/ 目录 (虚拟文件系统(virtual filesystem)，存放内核运行时的参数、网络信息、进程状态等数据到内存中)

| index            | introductions                     |
| ---------------- | --------------------------------- |
| /proc/\[0-9\]+/  | 该目录下以数字命名的文件夹是用于存储运行进程信息,目录名为 PID |
| /proc/meminfo    | 记录物理内存、交换空间等信息                    |
| /proc/loadavg    | 记录系统负载                            |
| /proc/uptime     | 记录系统运行时间                          |
| /proc/cpuinfo    | CPU 信息                            |
| /proc/modules    | 系统已加载的模块或驱动                       |
| /proc/mounts     | 文件系统挂载信息                          |
| /proc/swaps      | swap 分区信息                         |
| /proc/partitions | 系统分区信息                            |
| /proc/version    | 内核版本                              |
| /proc/stat       | CPU 利用率,磁盘,内存页                    |
| /proc/devices    | 可用的设备驱动列表                         |

#### /proc/net/ 目录 (网络协议信息)

| index              | introductions       |
| ------------------ | ------------------- |
| /proc/net/tcp      | 存储 TCP 连接信息文件       |
| /proc/net/udp      | 存储 UDP 连接信息文件       |
| /proc/net/arp      | ARP(协议及应用地址解析协议)信息表 |
| /proc/net/dev      | 统计网络实时数据流量          |
| /proc/net/snmp     | 网络传输协议的收发包信息        |
| /proc/net/sockstat | socket 使用记录         |
| /proc/net/netstat  | 网络数据统计              |
| /proc/net/route    | 路由表                 |

#### /proc/sys/ 目录 (更改各种不同的内核参数，所以修改这些文件要特别小心)

| index             | introductions                   |
| ----------------- | ------------------------------- |
| /proc/sys/fs/     | 文件系统各方面信息文件夹，如配额、文件句柄、inode和目录项 |
| /proc/sys/kernel/ | 内核参数文件夹                         |
| /proc/sys/net/    | 网络配置信息文件夹，如以太网、ipx、ipv4和ipv6    |
| /proc/sys/vm/     | 内核交换空间文件夹                       |

#### /etc/sysctl.conf (系统调优)

| index                                          | introductions                          |
| ---------------------------------------------- | -------------------------------------- |
| fs.file-max = 655360                           | 内核分配所有进程最大打开文件句柄数量                     |
| fs.suid_dumpable = 0                           | 不生成core文件                              |
| kernel.pid_max = 65535                         | 允许用户创建的最大进程数                           |
| kernel.kptr_restrict = 1                       | 此功能为安全性功能，防止泄露内核地址                     |
| kernel.randomize_va_space = 2                  | 设置进程虚拟地址空间的随机化                         |
| kernel.msgmnb = 65535                          | 设置单个消息队列中允许的最大字节长度                     |
| kernel.msgmax = 65535                          | 设置消息队列中单个消息的最大字节数                      |
| kernel.shmmni = 4096                           | 设置共享内存段最大数量数目                          |
| vm.swappiness = 0                              | 内核按此值百分比来使用swap，0为尽可能不使用swap           |
| vm.vfs_cache_pressure = 50                     | 内核回收用于directory和inode cache内存的倾向       |
| vm.dirty_background_ratio = 2                  | 内核flusher线程开始清理磁盘写缓存的上限                |
| vm.dirty_ratio = 3                             | 磁盘写缓存上限（占总内存的百分比）                      |
| vm.min_free_kbytes = 131072                    | 强制Linux VM最低保留的内存大小(以KB计算)             |
| vm.page-cluster=3                              | 参数控制一次写入或读出swap分区的页面数量                 |
| vm.block_dump=0                                | 启用块I/O调试                               |
| vm.overcommit_memory=1                         | 允许内存的过量分配                              |
| net.ipv4.tcp_congestion_control = westwood     | 设置TCP拥塞控制算法                            |
| net.core.somaxconn = 1024                      | 每个端口最大监听队列长度                           |
| net.ipv4.tcp_timestamps = 1                    | 启用更精确的方法对 RTT 的计算                      |
| net.ipv4.tcp_no_metrics_save = 1               | TCP会在连接关闭时保存各种连接信息到路由缓存中               |
| net.ipv4.tcp_moderate_rcvbuf = 1               | 接收数据时调整接收缓存                            |
| net.ipv4.tcp_window_scaling = 1                | 设置tcp/ip会话的滑动窗口大小可以变动                  |
| net.ipv4.tcp_rfc1337 = 1                       | 开启内核在TIME-WAIT中为套接字丢弃RST数据包            |
| net.ipv4.route.flush = 1                       | 刷新路由高速缓冲                               |
| net.ipv4.ip_no_pmtu_disc = 0                   | 在全局范围内关闭路径MTU探测功能                      |
| net.ipv4.tcp_fastopen = 1                      | 启用TCP(draft-ietf-tcpm-fastopen)功能来发送数据 |
| net.ipv4.tcp_slow_start_after_idle = 0         | 禁用后，拥塞窗口在空闲时间不会超时                      |
| net.ipv4.tcp_sack = 1                          | 选择性地应答，乱序接收到的报文来提高性能                   |
| net.ipv4.tcp_fack = 1                          | 打开FACK拥塞避免和快速重传功能                      |
| net.ipv4.tcp_ecn = 0                           | 禁止TCP的直接拥塞通告功能                         |
| net.ipv4.tcp_low_latency = 1                   | 允许TCP/IP栈适应在高吞吐量情况下低延时的情况              |
| net.ipv4.tcp_frto = 2                          | TCP堆栈调整有损无线网络                          |
| net.core.rmem_max = 8388608                    | 设置 socket 接收最大缓冲区大小                    |
| net.core.wmem_max = 8388608                    | 设置 socket 发送最大缓冲区大小                    |
| net.core.rmem_default = 8388608                | 设置 socket 接收默认缓冲区大小,单位字节               |
| net.core.wmem_default = 8388608                | 设置 socket 发送默认缓冲区大小                    |
| net.core.optmem_max = 40960                    | 设置 socket 允许最大缓冲区大小                    |
| net.ipv4.tcp_rmem = 4096 87380 8388608         | 预留用于接收缓冲的内存最小值、内存数量、内存最大值              |
| net.ipv4.tcp_wmem = 4096 65536 8388608         | 预留用于发送缓冲的内存最小值、内存数量、内存最大值              |
| net.ipv4.ip_local_port_range = 1024 65535      | 指定使用本地 TCP 或 UDP 端口范围                  |
| net.ipv4.ip_forward = 0                        | 关闭系统接口转发数据包                            |
| net.ipv4.conf.all.forwarding = 0               | 禁止接口打开转发功能                             |
| net.ipv4.conf.default.forwarding = 0           | 禁止接口打开转发功能                             |
| net.ipv4.conf.all.accept_redirects = 0         | 禁止收发接收ICMP重定向消息                        |
| net.ipv4.conf.default.accept_redirects = 0     | 禁止收发接收ICMP重定向消息                        |
| net.ipv4.conf.all.secure_redirects = 0         | 禁止收发接收给默认网关列表中网关的ICMP重定向消息             |
| net.ipv4.conf.default.secure_redirects = 0     | 禁止收发接收给默认网关列表中网关的ICMP重定向消息             |
| net.ipv4.conf.all.send_redirects = 0           | 禁止发送重定向消息                              |
| net.ipv4.conf.default.send_redirects = 0       | 禁止发送重定向消息                              |
| net.ipv4.conf.all.accept_source_route = 0      | 接收带有SRR选项的数据报，主机设为0，路由设为1              |
| net.ipv4.conf.default.accept_source_route = 0  | 接收带有SRR选项的数据报，主机设为0，路由设为1              |
| net.ipv4.icmp_echo_ignore_all = 1              | 设置忽略 icmp 响应包和广播包                      |
| net.ipv4.icmp_echo_ignore_broadcasts = 1       | 设置忽略 icmp 响应包和广播包                      |
| net.ipv4.icmp_ignore_bogus_error_responses = 1 | 设置忽略广播帧发送伪造的响应                         |
| net.ipv4.tcp_syncookies = 0                    | 关闭TCP同步标签(syncookie)                   |
| net.ipv4.conf.default.rp_filter = 1            | 通过反向路径回溯进行源地址验证                        |
| net.ipv4.conf.all.rp_filter = 1                | 允许多个网络介质位于同一子网段内                       |
| net.ipv4.tcp_synack_retries=2                  | 远端连接请求SYN，内核会发送SYN+ACK数据报，确认收到SYN连接请求  |
| net.ipv4.tcp_syn_retries=2                     | 本机向外发起TCP SYN连接超时重传的次数                 |
| net.ipv4.tcp_max_syn_backlog=1024              | listen 函数的backlog参数                    |
| net.ipv4.tcp_max_tw_buckets=16384              | 服务器TIME-WAIT状态套接字的数量限制                 |
| net.ipv4.tcp_fin_timeout=15                    | 服务器一个socket 在FIN-WAIT2 状态维护的时间         |
| net.ipv4.tcp_keepalive_time=60                 | 从最后一个包结束后多少秒内没有活动，才发送keepalive包保持连接    |
| net.ipv4.tcp_keepalive_intvl = 10              | 发送TCP探测的频率                             |
| net.ipv4.tcp_keepalive_probes = 6              | 丢弃TCP连接前，进行最大TCP保持连接侦测的次数              |
| net.ipv4.udp_rmem_min=6144                     | 这个值在一定程度上影响了并发量，需要根据具体业务来调整            |
| net.ipv4.udp_wmem_min=6144                     | 这个值在一定程度上影响了并发量，需要根据具体业务来调整            |
| net.unix.max_dgram_qlen=50                     | 允许域套接字中数据包的最大个数                        |
| net.core.netdev_max_backlog = 65536            | 设置个别接口接收包的速度快于内核处理速度时允许的最大的包序列         |
| net.ipv4.tcp_mtu_probing = 1                   | 开启tcp层路径mtu发现，自动调整tcp窗口                |

```
#!/bin/bash/
sudo chmod 777 /etc/sysctl.conf
cat > /etc/sysctl.conf <<EOF
fs.file-max = 655360
fs.suid_dumpable = 0
kernel.pid_max = 65535
kernel.kptr_restrict = 1
kernel.randomize_va_space = 2
kernel.msgmnb = 65535
kernel.msgmax = 65535
kernel.shmmni = 4096
vm.swappiness = 0
vm.vfs_cache_pressure = 50
vm.dirty_background_ratio = 2
vm.dirty_ratio = 3
vm.min_free_kbytes = 131072
vm.page-cluster=3
vm.block_dump=0
vm.overcommit_memory=1
net.ipv4.tcp_congestion_control = westwood
net.core.somaxconn = 1024
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_no_metrics_save = 1
net.ipv4.tcp_moderate_rcvbuf = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_rfc1337 = 1
net.ipv4.route.flush = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_fastopen = 1
net.ipv4.tcp_slow_start_after_idle = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_ecn = 0
net.ipv4.tcp_low_latency = 1
net.ipv4.tcp_frto = 2
net.core.rmem_max = 8388608
net.core.wmem_max = 8388608
net.core.rmem_default = 8388608
net.core.wmem_default = 8388608
net.core.optmem_max = 40960
net.ipv4.tcp_rmem = 4096 87380 8388608
net.ipv4.tcp_wmem = 4096 65536 8388608
net.ipv4.ip_local_port_range = 1024 65535
net.ipv4.ip_forward = 0
net.ipv4.conf.all.forwarding = 0
net.ipv4.conf.default.forwarding = 0
net.ipv4.conf.all.accept_redirects = 0
net.ipv4.conf.default.accept_redirects = 0
net.ipv4.conf.all.secure_redirects = 0
net.ipv4.conf.default.secure_redirects = 0
net.ipv4.conf.all.send_redirects = 0
net.ipv4.conf.default.send_redirects = 0
net.ipv4.conf.all.accept_source_route = 0
net.ipv4.conf.default.accept_source_route = 0
net.ipv4.icmp_echo_ignore_all = 1
net.ipv4.icmp_echo_ignore_broadcasts = 1
net.ipv4.icmp_ignore_bogus_error_responses = 1
net.ipv4.tcp_syncookies = 0
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.all.rp_filter = 1
net.ipv4.tcp_synack_retries=2
net.ipv4.tcp_syn_retries=2
net.ipv4.tcp_max_syn_backlog=1024
net.ipv4.tcp_max_tw_buckets=16384
net.ipv4.tcp_fin_timeout=15
net.ipv4.tcp_keepalive_time=60
net.ipv4.tcp_keepalive_intvl = 10
net.ipv4.tcp_keepalive_probes = 6
net.ipv4.udp_rmem_min=6144
net.ipv4.udp_wmem_min=6144
net.unix.max_dgram_qlen=50
net.core.netdev_max_backlog = 65536
net.ipv4.tcp_mtu_probing = 1
#net.ipv6.route.flush = 1
#net.ipv6.conf.all.disable_ipv6 = 1
#net.ipv6.conf.default.disable_ipv6 = 1
#net.ipv6.conf.lo.disable_ipv6 = 1
EOF
#Then reload sysctl configurations
#sudo sysctl -p
```
