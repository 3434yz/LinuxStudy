## 服务Service管理

服务service本质就是进程，但是是运行在后台的，通常监听某个端口，等待其他程序请求。

### service管理命令

* service 服务名 [start|stop|restart|reload|status]
* 在centos7后 很多服务不再使用service，而是systemctl
* service指令管理的服务在/etc/init.d查看

### chkconfig指令

通过chkconfig可以给服务的各个运行级别设置自 启动/关闭

chkconfig指令管理的服务在/etc/init.d 查看

centos7.0之后很多服务使用systemctl管理

#### chkconfig基本用法

* 查看服务 chkconfig --list [| grep xxx]
* chkconfig 服务名 --list
* chkconfig --level 运行级别 服务名 on/off

## systemctl管理命令

* systemctl [ start| stop| restart| status] 服务名
* systemctl指令管理的服务在 /usr/lib/systemd/system 查看

### systemctl设置服务的自启动状态

* systemctl list-unit-files [grep xxx] 查看服务开机启动状态
* systemctl enable 服务名(设置服务开机启动)
* systemctl disable 服务名(关闭服务开机启动)
* systemctl is-enable 服务名(查看某个服务是否是自启动的)

systemctl runlevel3和5一样

## 打开或者关闭指定端口

在真正的生产环境，往往需要将防火墙打开，但问题来了，如果我们将防火墙打开，那么外部请求的数据包就不能跟服务器监听端口通讯。这时需要打开指定端口。比如80、22、8080等

### firewall指令

打开端口: firewall-cmd --permanent --add-port=端口/协议

关闭端口: firewall-cmd --permanent --remove-port=端口号/协议

重新载入,才能生效： firewall-cmd --reload

查询端口是否开放:	  firewall-cmd --query-port=端口/协议


## 动态监控进程

指令 top

| 选项 | 功能                                       |
| ---- | ------------------------------------------ |
| -d   | 指定top命令的更新间隔，默认3s              |
| -i   | 使top不显示任何闲置或者僵死的进程          |
| -P   | 通过指定监控进程ID来仅仅监控某个进程的状态 |

**top - 13:56:52 up  7:29,  3 users,  load average: 0.00, 0.01, 0.05
Tasks: 144 total,   1 running, 143 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  3861264 total,  2055264 free,   458968 used,  1347032 buff/cache
KiB Swap:  2097148 total,  2097148 free,        0 used.  3118800 avail Mem**

load average后面的三个值总和除以三大于0.7的情况下说明负载比较大

主要交互：P（以CPU排序）、M（以内存排序） 、K（杀死某个进程)、u（某个用户)


### 监控网络状态:netstat -anp | more
