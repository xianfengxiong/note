# GC相关

GC日志的意义：

youngGC

![](/assets/youngGC.jpg)

fullGC

![](/assets/fullGC.jpg)

怎么开启gc日志

1.运行java程序时，使用额外的参数 

-XX:PrintGC                                    输出GC日志

-XX:+PrintGCDetails                        输出GC详细信息

 -XX:+PrintGCTimeStamps              输出GC的时间戳

-Xloggc:\/var\/log\/java\/gc.log            日志文件的输出路径



2.如果java程序运行时没有设置gc日志开关参数，可以使用jinfo工具改变java程序运行时的参数

i. jps        查找java进程id   

ii. jinfo -flag +PrintGC  pid   

iii. jinfo -flag +PrintGCDetails pid

iv.jinfo -flag +PrintGCTimeStamps pid

这时候GC日志就开启了，日志文件默认在标准输出

