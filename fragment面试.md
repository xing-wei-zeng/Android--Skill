#Fragment面试
##Fragment为什么被称为第五大组件
####Fragment为什么被称为第五大组件
 - 使用频率上Fragment不属于其它四大组件，拥有自己的生命周期
 - 可以动态灵活加载布局
####Fragment加载到Activity的两种方式
 - 静态加载 将Fragment到Acitivity的布局文件中
 - 动态加载 在activity中添加fragment
 - (一：添加一个FragmentManager的实例 )
 - (二：用add()方法加上Fragment的对象rightFragment)
 - (三：调用commit()方法使得FragmentTransaction实例的改变生效)
####FragmentPagerAdapter与FragmentStatePagerAdapter区别
 - FragmentStatePagerAdapter在每次切换页面的时候是回收内存的所以适合在页面比较多的情况
##Fragment生命周期
![fragment](https://i.loli.net/2018/04/07/5ac8c0a00c4c4.png)
![fragment](https://i.loli.net/2018/04/07/5ac8c1327e8e8.jpg)
##Fragment之间的通信
 - 在Fragment中调用Activity中的方法getActivity()
 - 在Activity中调用Fragment中的方法 接口回调 ，Fragment写一个接口，由Activity实现
 - 在Fragment中调用Fragment中的方法 findFragmentById()
##Fragment管理器：FragmentManager
 - Fragment的replace、add、remove方法