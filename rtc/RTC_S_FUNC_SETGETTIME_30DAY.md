**测试用例**  
RTC_S_FUNC_SETGETTIME_30DAY  

**测试概述**  
以可读可写模式打开/dev/rtc0，将rtc0当前时间设置2000-4-30的23:59:57，进行跨月份的测试  

**测试工具**  
rtc_tests  

**测试方法**  
```
$ ./opt/ltp/runltp -P light-evm -f ddt/rtc_setgettime -s RTC_S_FUNC_SETGETTIME_30DAY
```
实际运行:  
```
$ rtc_tests -device $DEV_NODE  -ioctltest setgettime -ioctltestarg 1
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
1. 以可读可写方式打开/dev/rtc0设备  
    	a) 默认打开为/dev/rtc0  
	b) 若打开失败则输出失败信息，退出测试用例，测试失败  
2. 设置rtc0当前时间为2000-4-30的23:59:57，延时5s，查看当前时间是否准确  
	a) 若设置当前rtc0时间失败，退出测试用例，测试失败  
	b) 拿设置的时间加上5s与延迟5s后获取的时间做判比，相同则测试成功，不相同则测试失败  
3. 若以上步骤执行成功，则本条测试用例测试PASS  
