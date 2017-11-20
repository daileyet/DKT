---
JAVA VM Options

---

Java启动参数分三类:

1. 标准参数 ( - )
2. 非标准参数 ( -X )
3. 非Stable参数 ( -XX )





### -X

#### -Xincgc

表示采用渐进式垃圾回收

#### -Xmsn

设置初始内存池大小,n是要设置的值，必须是1024

-Xms512m  设置JVM促使内存为512m。

此值可以设置与-Xmx相同，以避免每次垃圾回收完成后JVM重新分配内存

#### -Xmxn

表示内存池允许的最大大小,n是要设置的值，必须是1024

-Xmx512m ，设置JVM最大可用内存为512M。

#### -Xmnn

设置年轻代大小

-Xmn200m：设置年轻代大小为200M。整个堆大小=年轻代大小 + 年老代大小 + 持久代大小。持久代一般固定大小为64m，所以增大年轻代后，将会减小年老代大小。此值对系统性能影响较大，Sun官方推荐配置为整个堆的3/8。

#### -Xssn

线程栈大小,n是要设置的值，必须是1024



### 查看内存占用

#### JAVA代码

```java
//最大可用内存，对应-Xmx
Runtime.getRuntime().maxMemory(); 
//当前JVM空闲内存
Runtime.getRuntime().freeMemory(); 
//当前JVM占用的内存总数，其值相当于当前JVM已使用的内存及freeMemory()的总和
Runtime.getRuntime().totalMemory(); 
```

关于maxMemory()，freeMemory()和totalMemory()：

maxMemory()为JVM的最大可用内存，可通过-Xmx设置，默认值为物理内存的1/4，设值不能高于计算机物理内存；

totalMemory()为当前JVM占用的内存总数，其值相当于当前JVM已使用的内存及freeMemory()的总和，会随着JVM使用内存的增加而增加；

freeMemory()为当前JVM空闲内存，因为JVM只有在需要内存时才占用物理内存使用，所以freeMemory()的值一般情况下都很小，而 JVM实际可用内存并不等于freeMemory()，而应该等于maxMemory()-totalMemory()+freeMemory()。及其 设置JVM内存分配

#### jmap 

(linux下特有，也是很常用的一个命令),观察运行中的jvm物理内存的占用情况。

　　参数如下：

　　-heap ：打印jvm heap的情况

　　-histo： 打印jvm heap的直方图。其输出信息包括类名，对象数量，对象占用大小。

　　-histo：live ： 同上，但是只答应存活对象的情况

　　-permstat： 打印permanent generation heap情况