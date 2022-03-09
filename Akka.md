# 什么是 Akka

Akka是JAVA虚拟机JVM平台上构建高并发、分布式和容错应用的工具包和运行时,是一个框架。**Akka用Scala语言写成**，同时提供了Scala和JAVA的开发接口。

Akka处理并发的方法基于Actor模型。**在Akka里，Actor之间通信的唯一机制就是消息传递。** 

# 什么是 Actor

**Actor是Akka中最核心的概念**，它是一个封装了**状态和行为**的对象，Actor之间可以通过交换消息的方式进行通信，**每个Actor都有自己的收件箱（Mailbox）。** 

> 维基百科：在计算科学领域，Actor模型是一个并行计算（Concurrent Computation）模型，它把actor作为并行计算的基本元素来对待：为响应一个接收到的消息，一个actor能够自己做出一些决策，如创建更多的actor，或发送更多的消息，或者确定如何去响应接收到的下一个消息。 

通过Actor能够简化锁及线程管理，可以非常容易地开发出正确地并发程序和并行系统，Actor具有如下特性：

- 提供了一种高级抽象，能够简化在并发（Concurrency）/并行（Parallelism）应用场景下的编程开发
- 提供了异步非阻塞的、高性能的事件驱动编程模型
- 超级轻量级事件处理（每GB堆内存几百万Actor）

**actorOf：**调用ActorSystem的actorOf方法创建一个Actor实例，**返回一个引用ActorRef**，它包括一个UID和一个Path，标识了一个Actor，可以通过该引用向该Actor实例发送消息。

**ActorSystem：**在Akka中，一个ActorSystem是一个**重量级的结构**，他需要分配多个线程，所以在实际应用中，按照逻辑划分的每个应用对应一个ActorSystem实例。

**Supervisor：**ActorSystem是具有分层结构（Hierarchical Structure）的：一个Actor能够管理（Oversee）某个特定的函数，**他可能希望将一个task分解为更小的多个子task，这样它就需要创建多个子Actor（Child Actors），并监督这些子Actor处理任务的进度等详细情况**，实际上这个Actor创建了一个Supervisor来监督管理子Actor执行拆分后的多个子task，如果一个子Actor执行子task失败，那么就要向Supervisor发送一个消息说明处理子task失败。需要知道的是，==一个Actor能且仅能有一个Supervisor，就是创建它的那个Actor==。基于被监控任务的性质和失败的性质，一个Supervisor可以选择执行如下操作选择：

1. 重新开始（Resume）一个子Actor，保持它内部的状态。
2. 重启一个子Actor，清除它内部的状态。
3. 终止一个子Actor。
4. 扩大失败的影响，从而使这个子Actor失败。

将一个Actor以一个监督层次结构视图来看是非常重要的，因为它诠释了上面第4种操作选择的存在性，而且对前3种操作选择也有影响：**重新开始**（Resume）一个Actor，则该Actor的所有子Actor都继续工作；**重启一个Actor**，则该Actor的所有子Actor都被重新启动；**终止一个Actor，**则该Actor的所有子Actor都被终止。另外，一个Actor的preRestart方法的默认行为是终止所有子Actor，如果我们不想这样，可以在继承Actor的实现中重写preRestart方法的逻辑。

# 什么是 Cluster

Akka Cluster提供了一个容错（Fault-Tolerant）、==去中心化（Decentralized）、基于P2P的集群服务==，而且不会出现单点故障（SPOF， Single Point Of Failure）。Akka基于Gossip实现集群服务，而且支持服务自动失败检测。 

==一个Akka集群由一组成员节点组成，每个成员节点通过hostname:port:uid来唯一标识==，并且每个成员节点之间是解耦合的（Decoupled）。 

一个Akka应用程序是一个**分布式应用程序**，它具有一个Actor的集合S，而每个节点上可以启动这个Akka应用S的集合的的一部分Actor，而不必是全集S。 

如果一个新的成员节点需要加入到Akka集群，只需要在集群中**任意一个成员节点**上执行Join命令即可。 

Akka集群中任何一个成员节点都有可能成为集群的Leader，Leader只是一种角色，在各轮Gossip收敛过程中Leader是不断变化的。**Leader的职责是使成员节点进入/离开集群**。 













