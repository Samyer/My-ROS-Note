# My-ROS-Note
About Learning ROS notes and attention
>学习ROS遇到的问题及其解决办法和注意事项<br>
1.ROS编译工作空间(catkin_make)和packages功能包错误<br>
>>按照ROS教程，创建工作空间和编译工作空间，功能包步骤如下：<br>
    $ mkdir -p ~/catkin_ws/src<br>
    $ cd ~/catkin_ws/src<br>
    $ cd ~/catkin_ws/<br>
    $ catkin_make<br>
出现如下错误：<br>
![image1](https://img-blog.csdn.net/20170728103604158?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvSmExcjA=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
![image2](https://img-blog.csdn.net/20170728103604158?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvSmExcjA=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
解决过程：<br>
这是由于系统的python编译器版本与ROS所用的python编译器版本不一致<br>
比如：python版本为3.6而ROS用的是2.7<br>
我默认的python编译器是anaconda<br>
$python --version<br>
Python 3.6.4 :: Anaconda custom (64-bit)<br>
现在必须将系统默认编译器改为python2.7<br>
打开文件<br>
$gedit ~/.bashrc<br>
将下面这句设定默认使用anaconda的语句删除或在前面加“#”号注释：<br>
重新打开终端生效：<br>
$python --version<br>
Python 2.7.12<br>
再删除原来创建的ROS工作空间，按ROS教程上重新创建工作空间执行catkin_make则编译成功！<br>
'注意：由于修改了python默认编译器为2.7所以原来安装的pytorch将不能正常运行，要使用pytorch必须要将<br>
~/.bashrc文件里的环境变量改回来。'<br>
