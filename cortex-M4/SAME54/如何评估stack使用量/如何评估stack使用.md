
# 1.在链接文件中修改相应代码，使得芯片在初始化的时候将stack内容全部写成0x55
```
	/* set the stack as "0x55"  */
        for (pDest = &_sstack; pDest < &_estack;) {
                *pDest++ = 0x55555555;
        }
```
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/%E5%A6%82%E4%BD%95%E8%AF%84%E4%BC%B0stack%E4%BD%BF%E7%94%A8%E9%87%8F/reference/stack_evaluation_001.png)


# 2.在map文件中找到stack的起始地址（注意：编译器会根据实际的工程分配一段空间给全局变量）
从下图可以看出，实际编译器分配了0x20000000 ~ 0x200000a0这段空间给全局变量，所以stack空间分配的时候有个偏移地址
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/%E5%A6%82%E4%BD%95%E8%AF%84%E4%BC%B0stack%E4%BD%BF%E7%94%A8%E9%87%8F/reference/stack_evaluation_002.png)


# 3.在链接文件中看实际的stack大小
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/%E5%A6%82%E4%BD%95%E8%AF%84%E4%BC%B0stack%E4%BD%BF%E7%94%A8%E9%87%8F/reference/stack_evaluation_003.png)

# 4.调试看实际的SRAM的分配关系（注意：这里有0xA0的地址便宜）
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/%E5%A6%82%E4%BD%95%E8%AF%84%E4%BC%B0stack%E4%BD%BF%E7%94%A8%E9%87%8F/reference/stack_evaluation_004.png)

# 5.运行代码一段时间，看有stack剩余多少地址没有被改，这样就可以评估除用了多少stack空间了。
