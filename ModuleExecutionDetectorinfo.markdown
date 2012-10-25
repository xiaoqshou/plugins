#OSMonitor.h

* s2e在OSMonitor.h中定义了OSMonitor类，在该类中定义了所有OSMonitor都会用到的信号量，如下： 

* 信号：

* WindowsMonitor继承了该类

#WindowsMonitor

* 该插件实现了对模块和进程加载和卸载的监视，其他插件称其为Intercepter。

* 信号：

#ModuleExecutionDetector

* 通过发送信号表明执行状态何时进入和离开我们所感兴趣的module.必然依赖OSMonitor

* 信号：



