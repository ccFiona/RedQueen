# 代理模式
玩过扮白脸、扮黑脸的游戏吗？这就是代理要做的：控制和管理访问。

## 还记得状态模式的那台糖果机吗？现在我们需要远程监控糖果机。(在开始编码之前，需要收集需求)。

## 远程代理
- 远程代理就好比“远程对象的本地代表”。何谓“远程对象“？这是一种对象，活在不同的Java虚拟机(JVM)堆中。
- 你的客户对象所做的就像是在做远程方法调用，但其实只是调用本地堆中的”代理“上的方法，再由代理处理所有网络通信的低层细节。
- 中间还穿插了一定的RMI(remote mothod invoke)

## 代理过程
- 1.CEO执行监视器，先取得远程糖果机的代理，然后调用每个代理的getState()。
- 2.代理上的getState()被调用，此调用被转发到远程服务。Skeleton接受到请求，然后转发给糖果机。
- 3.糖果机将状态返回给skeleton，skeleton将状态序列化，通过网络传回给代理，代理将其反序列化，把他当做一个对象返回给监视器。

## 代理模式
<font color="red">为另一个对象提供一个替身或占位符以控制对这个对象的访问。</font>

### 使用代理模式创建代表(representative)对象，让代表对象控制某对象的访问，被代理的对象可以是远程对象、创建开销大的对象或需要安全控制的对象。

## 虚拟代理
显示CD封面
- 先给个虚拟的CD(CD封面加载中请稍后。。。)
- 再开个线程异步的下载CD.jpg一旦加载完成，代理就把显示的职责委托给Icon。
加载图像和ImageIcon是同步的(synchronous)，也就是说，只有在加载完之后，ImageIcon构造器才会返回。这样，我们的程序会耗在这里，动弹不得，也没有办法显示消息，所以要把加载变成异步(asynchronous)。

## 保护代理
对象村的约会系统，确保一个对象的方法，让不同权限的人是否可以访问？

## 还有代理模式的变体：防火墙代理、缓存代理、同步代理、写入时复制代理。。。

## 要点
- 远程代理管理客户和远程对象之间的交互。
- 虚拟代理控制访问实例化开销大的对象。
- 保护代理基于调用者控制对象方法的访问。
- 代理在结构上类似装饰者，但是目的不同。
- 装饰者模式为对象加上行为，而代理则是控制访问。
- Java内置的代理支持，可以根据需要建立动态代理，并将所有调用分配的所选的处理器。