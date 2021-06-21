**测试用例**  
DMA_DMATEST_CHANNEL_128_64K_buff_size_1  

**测试概述**  
检测DMA通道的读写功能和性能（DMA通道：dma0chan0，通道宽度：128bit，传输总字节：64K）  

**测试工具**  
dmatest  

**测试方法**  
```
$ ./runltp -P light-evm -f ddt/dma_kernel -s DMA_DMATEST_CHANNEL_128_64K_buff_size_1
```

**实际运行**  
```
$ DMA_DMATEST_CHANNEL_128_64K_buff_size_1 source 'dma0chan0.sh'
dma0chan0.sh：
$ echo 1 > /sys/module/dmatest/parameters/noverify
$ echo 1 > /sys/module/dmatest/parameters/norandom
$ echo 1 > /sys/module/dmatest/parameters/iterations
$ echo 4 > /sys/module/dmatest/parameters/alignment
$ echo 65536 > /sys/module/dmatest/parameters/test_buf_size
$ echo dma0chan0 > /sys/module/dmatest/parameters/channel
$ echo 1 > /sys/module/dmatest/parameters/run
dma0chan0.sh帮助：
        noverify        禁用随机验证（默认：开启）
        norandom        禁用随机偏移设置（默认：开启）
        iterations      测试的循环次数
        alignment       字节对齐（默认：不使用，-1）
        test_buf_size   拷贝时的buffer大小（字节）
        channel         指定的dma测试通道
        run             指定加载模块时是否直接执行测试
        wait            指定加载模块执行测试用例时是否需要等待测试线程执行结束
```

**测试说明**  
1. 测试参数初始化  
        a) 初始化相关的参数（buffer大小，DMA通道，循环次数，超时时间等等）  
        b) run参数指定加载模块时直接执行测试  
2. 通道申请  
        a) 申请dma通道，根据测试的参数进行通道筛选  
	b) 当前DMA通道：dma0chan0，通道宽度：128bit，传输总字节：64K
        c) 保存通道到内部信息中，同时申请相关资源，失败时将通道资源释放并退出，测试fail  
3. 申请通道附加资源  
        a) 申请内存保存通道地址，将申请的资源保存到相关链表中  
4. DMA传输  
        a) 获取相关参数信息，为源和目的地址申请内存空间  
        b) 获取传输时的字节对齐，对buffer的长度进行字节对齐  
        c) 申请内存空间，映射要memcpy的源地址和目的地址  
        d) 申请tx描述符，描述符是一个单向列表，描述了每块数据的位置和大小还有其他配置（device_prep_dma_memcpy()）  
        e) DMA自行解析描述符的内容进行数据传输并寻找下一个链表节点  
        f) 等待传输完成，获取传输完成状态，传输超时或者传输过程出错都将释放资源  
        g) 数据校验以及时间统计，计算运行时间  
        h) 释放相关资源，终止通道的所有传输  
5. 停止传输  
        a) 遍历链表将所有链表资源进行释放，通道资源进行释放  
