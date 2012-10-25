###OSMonitor发出的信号

* onModuleLoad
> 产生时间：当模块加载时

* onModuleUnload
> 产生时间：当模块卸载时   

* onProcessUnload
> 产生时间：进程结束时

* onThreadCreate
> 产生时间：线程创建时

* onThreadExit
> 产生时间：线程结束时

* 与其他信号的关系：基本信号，所有OSMonitor类都要继承该类。都要用到以上信号。仅借口定义，无cpp。

###LibraryCallMonitor发出的信号

* onLibraryCall  

>  * 功能：捕获指定模块对导入的库函数的调用事件
>  * 产生此信号的函数：LibraryCallMonitor::onFunctionCall
>  * 产生时间：通过ModuleExecutionDetector 的 onModuleLoad 信号得到导入函数地址，连接连接 FunctionMonitor 插件的CallSignal 信号,进行相应处理,发送onLibraryCall 信号	
>  * 与其他信号的关系：依赖ModuleExecutionDetector 的 onModuleLoad 信号，FunctionMonitor的CallSignal 信号。

##WindowsMonitor类 重点分析类
===
* 继承OSMonitor,实现了对WindowsOS中模块的加载和卸载，进程的开始和结束以及线程的监控。

* 连接CorePlugin发出的信号：onTranslateInstructionStart信号和onPageDirectoryChange信号。

* 根据接收到的信号调用相应的处理函数，相应处理函数根据配置文件等发出相应继承OSMonitor的信号。

###KernelModeInterceptor
> 监控内核模式下模块的加载和卸载

###UserModeInterceptor
> 监控用户模式下模块的加载和卸载


###WindowsSpy
> 监控进程的开始和结束。

###WindowsImage
> 定义了windows内核中重要的数据结构 。

###WindowsCrashDumpGenerator
> 生成crash dump 文件。

###BlueScreenInterceptor
> ？？