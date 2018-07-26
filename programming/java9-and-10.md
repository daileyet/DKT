# Java9&10

## Java9新特性

### Java 平台模块系统

### Jshell

### 集合、Stream 和 Optional

### 进程 API

### 平台日志 API 和 服务

### 反应式流 （ Reactive Streams ）

### 变量句柄

### 改进方法句柄（Method Handle）

### 并发

### Nashorn

### I/O 流新特性

### 改进应用安全性能

### 用户界面

### 统一 JVM 日志

### 其他改动方面

1. Java 9 允许在接口中使用私有方法
2. 在 try-with-resources 语句中可以使用 e ffectively-final 变量
3. 类 java.lang.StackWalker 可 以对线程的堆栈进行遍历，并且支持过滤和延迟访问
4. Java 9 把对 Unicode 的支持升级到了 8.0
5. ResourceBundle 加载属性文件的默认编码从 ISO-8859-1 改成了 UTF-8，不再需要使用 native2ascii 命 令来对属性文件进行额外处理
6. 注解@Deprecated 也得到了增强，增加了 since 和 forRemoval 两 个属性，可以分别指定一个程序元素被废弃的版本，以及是否会在今后的版本中被删除

## Java10新特性

### 局部变量类型推断

### 整合 JDK 代码仓库

### 统一的垃圾回收接口

### 并行全垃圾回收器 G1

### 应用程序类数据共享

### 线程-局部管控

### 移除 Native-Header自动生成工具

### 额外的 Unicode 语言标签扩展

### 备用存储装置上的堆分配

### 基于 Java 的实验性 JIT 编译器

### 根证书认证

### 基于时间的版本发布模式

