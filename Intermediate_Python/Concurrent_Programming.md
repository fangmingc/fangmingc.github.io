# 并发编程
- [并发](#1)
- [进程](#2)
- [线程](#3)
- [协程](#4)
- [相关模块](#5)
	- [multiprocessing](#5.1)
	- [threading](#5.2)
	- [concorrent.futures](#5.3)
	- [gevent](#5.4)
	- [queue](#5.5)
- [相关扩展](#6)
	- [互斥锁](#6.1)
	- [生产者消费者模型](#6.2)
	- [回调函数](#6.3)
	- [I/O模型](#6.4)

## <span id="1">并发</span>
并发实现的核心原理:
- 任务之间的切换
- 保存任务切换前的状态

## <span id="2">进程</span>
进程的概念起源于操作系统，是操作系统最核心的概念。  

- 操作系统管理进程
- 进程之间的调度由操作系统的负责切换

### 概念
- 狭义定义
	- 进程是正在运行的程序的实例
	- 指的是程序的运行过程
- 广义定义
	- 计算机中的程序关于某数据集合上的一次运行活动，是系统进行资源分配和调度的基本单位，是操作系统结构的基础
- 含义的变更
	- 在早期面向进程设计的计算机结构中，进程是程序的基本执行实体
	- 在当代面向线程设计的计算机结构中，进程是线程的容器
- 主要特点
	1. 进程是一个实体   
	每一个进程都有它自己的地址空间，包括文本区域（text region）、数据区域（data region）、堆栈（stack region）
	2. 进程是一个执行中的程序   
	程序是一个没有生命的实体，只有处理器赋予程序生命时（操作系统执行之），它才能成为一个活动的实体

### 特征
1. 动态性   
进程的实质是程序在多道程序系统中的一次执行过程，动态产生，动态消亡
2. **并发性**   
伪并行，任何进程都可以同其他进程一起并发执行
3. 独立性   
进程是一个能独立运行的基本单位，同时也是系统分配资源和调度的独立单位
4. **异步性**   
由于进程间的相互制约，使进程具有执行的间断性，即进程按各自独立的、不可预知的速度向前推进
5. 结构特征   
进程由程序、数据和进程控制块三部分组成

### 状态
![](https://github.com/fangmingc/ChuannBlog/blob/master/Intermediate_Python/%E8%BF%9B%E7%A8%8B%E7%9A%84%E7%8A%B6%E6%80%81.png)
- 运行   
	1. 程序等待I/O，进入阻塞   
	2. 进程运行时间过长，调度程序选择另一个进程，该进程进入就绪  
- 就绪   
	3. 调度程序选择进程，进入运行  
- 阻塞  
	4. I/O操作出现结果，进入就绪  

## <span id="3">线程</span>
轻量级进程

### 特点
- 共享进程的数据  
- 创建开销小于创建进程开销

### 开线程的两种方式
- 直接实例化threading模块的Thread类，在参数指定线程任务  
- 自定义一个线程类，继承Thread类，在run函数定制任务

### 数据共享


## <span id="4">协程</span>


## <span id="5">相关模块</span>
### <span id="5.1">multiprocessing模块</span>
基本与threading相同
#### Process类
##### 实例化定义传入参数
- target   
指定进程的任务函数地址
- args   
指定任务函数的参数，元组格式传入
- kwargs   
指定任务函数的参数，字典格式传入
- callback   
指定回调函数地址

##### 方法
- start   
向操作系统发送进程开启请求(开进程必须有的方法)
- join   
主进程等待子进程结束
- terminate   
终止进程(该操作不会终止该进程的子进程)

##### 属性
- daemon  
	- True时设置子进程为主进程守护进程
	- 当主进程代码执行完毕，守护进程被回收
	- 必须在start方法启用前设定
- ident   
获取进程的id
- pid   
获取进程的id
##### 方法
- cpu_count   
查看计算机cpu数
- current_process   
获取当前进程对象，返回结果同Process类实例化对象

#### Pool类
- numprocess
设置的最大进程数
- initializer
- initargs

### <span id="5.2">threading模块</span>
#### Thread类
##### 实例化定义传入参数
- target   
指定进程的任务函数地址
- args   
指定任务函数的参数，元组格式传入
- kwargs   
指定任务函数的参数，字典格式传入
- callback   
指定回调函数地址

##### 方法   
- start
向操作系统发送线程开启请求(开线程必须有的方法)
- join
	- 主线程等待线程结束
	- 参数timeout，设定等待时间
- getName
获取当前线程名
- isDaemon   
判断当前线程是否是守护线程
- isAlive   
判断当前线程是否未结束

##### 属性
- daemon
	- True时设置线程为主线程的守护线程
	- 当主线程等待所有非守护线程结束后，守护线程被回收
	- 必须在startfan方法启用前使用
- name
当前线程名
- ident
当前线程id

#### Queue类
- 参数maxsize
队列允许的最大项数，省略则无限制
- put
	- 插入数据到队列中
	- 参数blocked 
		- False时，当Queue已满则抛出异常
	- 参数timeout
		- blocked为True时，当Queue已满时，阻塞指定时长，超时则抛出异常



#### Lock类
#### Manager类
#### Event类
#### Timer类
#### 方法
- currentThread
- get_ident
- activeCount
- enumerate
- main_thread

### <span id="5.3">concurrent.futures模块</span>
#### Executor类
#### ProcessPoolExecutor类
#### ThreadPoolExecutor类

### <span id="5.4">gevent模块</span>

### <span id="5.5">queue模块</span>
#### Queue类
#### LifoQueue类
#### PriorityQueue类

## <span id="6">相关扩展</span>
### <span id="6.1">互斥锁</span>
#### 原理
当一个进程/线程拿到数据使用权后，上一把锁，其余进程/线程看到数据被加锁就进入阻塞状态，直到锁被释放。
- 共享资源
	- 多个进程/线程的运行都是独立的，但是有可能出现对同一份资源的使用，这样的资源被称为共享资源
- 数据安全
	- 多个进程/线程同时对某一份共享资源，进行处理有可能会出现数据错乱
	- 例子中的资源是终端，最终打印出的数据就是乱的

	```python
	from multiprocessing import Process
	import os,time
	def work():
	    print('%s is running' %os.getpid())
	    time.sleep(2)
	    print('%s is done' %os.getpid())
	if __name__ == '__main__':
	    for i in range(3):
	        p=Process(target=work)
	        p.start()
	```

- 特点
	- ‘锁’可以保证共享资源的数据安全，在共享资源被锁住的期间，其他进程/线程不可以对共享数据操作
	- 同一时间只有一个进程/线程处理数据，牺牲了并发效果，变成了串行，保证了数据安全

#### 全局解释器锁（GIL）(Global Interpreter Lock)
- CPython特性
	- CPython的内存管理不是线程安全的。GIL已经存在，其他功能已经发展到依赖于它的实施。
- 每当一个Python脚本开启，首先会创建一个进程，其中必有一个主线程，但脚本想要运行肯定会运行解释器，解释器还带有一些线程，例如内存回收，如果不对数据加锁，就会产生数据正在被回收的时候其他线程，使用了该数据的情况，会导致数据错误
- GIL锁的作用级别是解释器级别，用户无法更改，但是需要了解这种机制

#### 死锁
- 百科定义
	- 死锁是指两个或两个以上的进程/线程在执行过程中，由于竞争资源或者由于彼此通信而造成的一种阻塞的现象，若无外力作用，它们都将无法推进下去。此时称系统处于死锁状态或系统产生了死锁，这些永远在互相等待的进程/线程称为死锁进程/线程。
- 四个必要条件
	1. **互斥条件** 指进程对所分配到的资源进行排它性使用，即在一段时间内某资源只由一个进程占用。如果此时还有其它进程请求资源，则请求者只能等待，直至占有资源的进程用毕释放。
	2. **请求和保持条件** 指进程已经保持至少一个资源，但又提出了新的资源请求，而该资源已被其它进程占有，此时请求进程阻塞，但又对自己已获得的其它资源保持不放。
	3. **不剥夺条件** 指进程已获得的资源，在未使用完之前，不能被剥夺，只能在使用完时由自己释放。
	4. **环路等待条件** 指在发生死锁时，必然存在一个进程——资源的环形链，即进程集合{P0，P1，P2，···，Pn}中的P0正在等待一个P1占用的资源；P1正在等待P2占用的资源，……，Pn正在等待已被P0占用的资源。
- 互斥锁引起的死锁
	- 当加锁资源超过两个且进程/线程超过两个
	- 一个进程/线程占有了A资源，进入等待B资源的阻塞状态，另一个进程/线程占有了B资源，进入等待A资源的阻塞状态，两个进程/线程互相处于阻塞对方所占有的资源的状态，且无法释放自己的资源，进入死锁状态
	- 解决办法 递归锁：RLock类
- 更广泛的死锁解决办法
	- 增加资源
	- 银行家算法

### <span id="6.2">生产者消费者模型</span>
- 共享资源
	- 概念 多个进程/线程的运行都是独立的，但是有可能出现对同一份资源的使用，这样的资源被称为共享资源
	- 关于数据交互 
		- IPC(进程间通信)
			- 队列Queue
			- 管道
		- 共享数据
			- Manager
- 生产者和消费者不直接交流，通过缓冲区交流，这是异步且并发的
- 缓冲区在Python中通常用消息队列实现

### <span id="6.3">回调函数</span>

### <span id="6.4">I/O模型</span>
#### 同步/异步/阻塞/非阻塞
- 同步/异步
	- 描述提交任务的规则
- 阻塞/非阻塞
	- 描述进程/线程的两种状态

#### 阻塞I/O
#### 非阻塞I/O
#### I/O多路复用
#### 异步I/O
#### 信号驱动I/O（不常用）