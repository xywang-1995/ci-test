**测试用例**  
RTC_S_FUNC_ALARM_0001  

**测试概述**  
延时30s测试rtc0 alarm  

**测试工具**  
rtc_tests  

**测试方法**  
```
$ ./opt/ltp/runltp -P light-evm -f ddt/rtc_alarm -s RTC_S_FUNC_ALARM_0001
```
实际运行:  
```
$ timeout 40 rtc_tests -device $rtc_node -ioctltest alarm -ioctltestarg 30
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
1. 默认以可读可写模式打开/dev/rtc0设备  
    	a) 默认打开/dev/rtc0  
	b) 若打开失败则输出失败信息，退出测试用例，测试失败  
2. 获取当前rtc0时间并加上30s作为设置alarm的时间参数  
	a) 若获取rtc0当前时间失败，退出测试用例，测试失败  
3. 设置alarm的时间  
	a) 若设置alarm失败，退出测试用例，测试失败  
4. 获取alarm的时间并判断是否设置成功  
	a) 判断读取的alarm时间是否与设置的alarm时间相同，不相同则退出测试用例，测试失败  
5. 打开alarm中断  
	a) 若打开失败，则退出测试用例，测试失败  
6. 等待alarm中断  
	a) 读取rtc0设备，若读取失败，则退出测试用例，测试失败  
	b) 若读取成功，则说明有alarm中断产生，并获取当前rtc0时间  
7. 关闭alarm中断  
	a) 判断关闭是否成功并拿步骤6获取的时间与设置的alarm时间相等，若不相等，则退出测试用例，测试失败  
8. 若以上步骤执行成功，则本条测试用例测试PASS  
