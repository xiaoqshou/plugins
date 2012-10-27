##OSMonitor 

* 定义五个信号

* 定义了一些虚函数

* 最基本内核事件接口

##Windows相关

###WindowsMonitor

* 继承OSMonitor,在windows版本下实现了OSMonitor中的基本接口

* 在Plugins/WindowsInterceptor文件夹下定义了一组对Windows系统事件进行监控和分析的插件，WindowsMonitor也在其中

##ModuleExecutionDetector

* 

* 

##LibraryCallMonitor

* 获取指定模块对导入库函数的调用事件  Flags all calls to external libraries

* 该插件依赖Interceptor,FunctionMonitor,ModuleExecutionDetector

		m_functionMonitor = static_cast<FunctionMonitor*>(s2e()->getPlugin("FunctionMonitor"));  
		m_monitor = static_cast<OSMonitor*>(s2e()->getPlugin("Interceptor"));
		m_detector = static_cast<ModuleExecutionDetector*>(s2e()->getPlugin("ModuleExecutionDetector")

* 连接ModuleExecutionDetector的onMoudleLoad信号、Interceptor的onModuleUnload信号，并调用相应的处理函数

     	m_detector->onModuleLoad.connect(sigc::mem_fun(*this,&LibraryCallMonitor::onModuleLoad));
   	    m_monitor->onModuleUnload.connect(sigc::mem_fun(*this,&LibraryCallMonitor::onModuleUnload));

*  *LibraryCallMonitor::onModuleLoad*  

>   功能：得到指定模块的导入函数，得到各导入函数的地址后，连接FunctionMonitor的Callsignal信号
>   *  
>   

