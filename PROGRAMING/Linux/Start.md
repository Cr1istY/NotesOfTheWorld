# Linux

## 第三章 Linux基础篇 - VM和Linux安装

### 1. 网络连接的三种模式

#### 1. 桥接模式

虚拟系统可以和外部系统相互通信，但是主机数量有限

当主机过多时，ip会产生冲突

#### 2. NAT模式

网络地址转换模式

虚拟机同主机互通，再通过主机进行外部通讯

可以避免ip冲突

#### 3. 仅主机模式

独立系统，不和外部发生联系

### 2. 虚拟机克隆

如果需要虚拟机集群时，不需要重新安装虚拟机，只需要进行克隆即可
