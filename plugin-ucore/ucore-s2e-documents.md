##编译最新版本s2e

	*.SDL问题，修改sdl.c:28,sdl_zoom.h:17,
	*.ok.我的电脑已经编译通过
	
##编译ucore

	*.测试
	*.常规流程
	
##plugin_Hostfile

	*.我理解为应该是加入该插件可以读取host主机中的host文件。
	*.参考赵静学长写的并行插件，里面用到来Hostfiles 它用的目的应该就是将种子文件保存到host下，并读取这些种子文件。 
		-- File: config.lua
		s2e = {
		  kleeArgs = {
		    -- Run each state for at least 1 second before
		    -- switching to the other:
		    -- "--use-batching-search=true", "--batch-time=1.0"
		    "--use-dfs-search=true", "--batch-time=1.0",
					  }
		}

		plugins = {
			  -- Enable a plugin that handles S2E custom opcode
			  "BaseInstructions",
			 "HostFiles",
			  "Cluster",
		}

		pluginsConfig = {}

		pluginsConfig.HostFiles = {
  		baseDir = "/root/Research/cluster/share"
		}
			*.todo
			
	根据赵旭给的提示在ucore里面看看读写文件永的是什么，编写例子查看一下
	最明显的结果是 不使用hostfiles 出错 使用后 ok....
		
##plugin_Edgekiller

	*.这个我暂时没有头绪啊，在去看看代码吧。
	*.看看例子，s2e自己带的例子还有他们已经写出来的例子。
