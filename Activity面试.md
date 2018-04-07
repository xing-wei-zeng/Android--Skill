#Activity面试详解
##activity生命周期
####activity的4种状态
 - running       paused       stopped       killed 
####activity生命周期的分析
![live](https://i.loli.net/2018/04/07/5ac86adc4f34f.jpg)
 - Activity启动  > onCreate() > onStart() > onResume()
 - 点击Home键回到主界面（Activity不可见） > onPause() > onStop()
 - 当再次回到原Activity时  > onRestart() > onStart() > onResume
 - 退出当前Acitivity时 > onPause()  > onStop()  > onDestrop()
####activity进程优先级
 - 前台/可见/服务/后台/空(低)
##android任务栈
![live](https://i.loli.net/2018/04/07/5ac872ee4e6ff.png)
##activity启动模式
 - standard ![live](https://i.loli.net/2018/04/07/5ac874e1e94ba.png)
 - singletop(栈顶复用模式) ![live](https://i.loli.net/2018/04/07/5ac8755543dee.png)
 - singletask(栈内复用模式,回调onNewIntent方法) ![live](https://i.loli.net/2018/04/07/5ac875dcd8310.png)
 - singleinstance ![live](https://i.loli.net/2018/04/07/5ac87678bc67e.png)
##scheme跳转协议
#####Android中的Scheme是一种页面内跳转协议，通过自定义Scheme协议，可以跳转到app中的任何页面
 - 服务器可以定制化跳转app页面
 - app可以通过Scheme跳转到另一个app页面
 - 可以通过h5页面跳转app原生页面
#####协议格式
 - Uri.parse("qh://test:8080/goods?goodsId=8897&name=fuck")
 - qh代表Scheme协议名称
 - test代表Scheme作用的地址域
 - 8080代表改路径的端口号
 - /goods代表的是指定页面(路径)
 - goodsId和name代表传递的两个参数