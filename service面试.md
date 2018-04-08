#Service面试
##service的应用场景，以及和Thread区别
####service是什么
 - Service(服务)是一个一种可以在后台执行长时间运行操作而没有用户界面的应用组件(里面不能做耗时操作)
####service和Thread的区别
 - service运行在主线程一定不能做耗时操作
 - Thread程序执行的最小单元
##开始service的两种方式以及区别
####startservice
 - 定义一个类继承Service
 - 在Manifest.xml文件中配置该service
 - 使用Cintext的startService(Intent)方法启动该Service
 - 不再使用时，调用stopService(Intent)方法停止该服务
####bindservice
 - 创建BindService服务端，继承自Service并在类中，创建一个实现IBinder接口的实例并提供公共方法给客户端调用
 - 从onBind()回调方法返回此Binder实例
 - 在客户端中，从onServiceConnected()回调方法接收Binder，并使用提供的方法调用绑定服务
