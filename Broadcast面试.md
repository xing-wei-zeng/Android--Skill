#Broadcast Receiver面试
##广播
####广播定义
 - Broadcast是一种广泛运用在应用程序直接传输信息的机制，要发送的广播内容就是一个Intent，这个Intent可以携带要传送的信息
####广播的使用场景
 - 同一个app具有多个进程的不同组件之间的消息通信
 - 不同aoo之间的组件之间的消息通信
####广播的种类
 - Normal Broadcast:Context.sendBroadcast
 - System Broadcast:Context.sendOrderedBroadcast
 - Local Broadcast:只在app内传播
##实现广播-receiver
 - 静态注册：注册完成就一直运行
 - 动态注册：跟随activity的生命周期
##广播内部实现机制
 - 自定义广播接收者BroadcastReceiver，并复写onRecvice()方法
 - 通过Binder机制向AMS（Activity Manager Service）进行注册
 - 广播发送者通过Binder进制向AMS发送广播
 - AMS查找符合条件（IntentFilter/Permission）的BroadcastReceiver,将广播发送到BroadcastReceiver(一般是Activity)相应的消息循环队列中
 - 消息循环执行拿到此广播，回调的BroadcastReceiver的onRecvice()方法
##LocalBroadcastManager详解
 - 使用它发送的广播只在app内传播，不用担心泄露隐私数据
 - 不必担心有安全漏洞可以利用
 - 比系统的全局广播更高效
 
 - LocalBroadcastManager对象的创建
 - LocalBroadcastManager localBroadcastManager = LocalBroadcastManager.getInstance( this ) ;
 - 注册广播接收器
 - LocalBroadcastManager.registerReceiver( broadcastReceiver , intentFilter );
 - 发送广播
 - LocalBroadcastManager.sendBroadcast( intent ) ;
 - 取消注册广播接收器
 - LocalBroadcastManager.unregisterReceiver( broadcastReceiver );
 
 - 在获取LocalBroadcastManager对象实例的时候，这里用了单例模式。并且把外部传进来的Context 转化成了ApplicationContext，有效的避免了当前Context的内存泄漏的问题。这一点我们在设计单例模式框架的时候是值得学习的，看源码可以学习到很多东西。
 - 在LocalBroadcastManager构造函数中创建了一个Handler.可见 LocalBroadcastManager 的本质上是通过Handler机制发送和接收消息的。