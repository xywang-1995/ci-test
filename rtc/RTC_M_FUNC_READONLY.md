**测试用例**  
RTC_M_FUNC_READONLY  

**测试概述**  
以只读模式打开/dev/rtc0设备，读取rtc0当前时间10次  

**测试工具**  
rtc_tests  

**测试方法**  
```
$ ./opt/ltp/runltp -P light-evm -f ddt/rtc_readonly -s RTC_M_FUNC_READONLY
```
实际运行:  
```
$ rtc_tests -device "$DEV_NODE" -loop 10 -ioctltest readtime -readonly
rtc_tests帮助:
	--options: 
		-device: 
   			rtc 驱动程序的设备节点名，默认/dev/rtc0 
 		-ioctltest:
 			readtime: 读取当前时间
 			setgettime: 写读时间
 			alarm: 获取当前时间并设置alarm
			NULL:
 		-ioclttestarg:
 			供ioclttest参数使用
 		-readonly:
 			以只读权限打开设备节点
 		-loop:
 			测试循环次数，测试内容则为对应的ioctltest的参数
```

**测试说明**  
1. 以只读模式打开/dev/rtc0设备  
    	a) 默认打开为/dev/rtc0    
	b) 若打开失败则输出失败信息，退出测试用例，测试失败  
2. 读取rtc0当前时间10次并打印  
	a) 读取时间成功则打印当前rtc0时间，失败则打印相应失败信息并退出测试，测试失败  
3. 若以上执行成功，本条测试用例测试PASS  
