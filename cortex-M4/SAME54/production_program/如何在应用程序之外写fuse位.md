# 工具说明 ： ATMEL studio
# 步骤1.
在XXXX_flash.ld文件中添加对user low section的说明
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/production_program/reference/fuse_002.png)
```
	/* User row section */
    .userRowBlock :{
        KEEP(*(.userrowsec))
    } > userrow
```

# 步骤2
在应用代码中添加对user low section的操作
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/production_program/reference/fuse_003.png)
```
// Method 2 to set fuse with user row section
__attribute__((section(".userrowsec"))) const uint32_t nvm_user_row[] =
{
	0xFFFF9239, // 0xFFFF9239, 0xFFFF9238
	0xAAA8FF80, // 0xAAA8FF80, 0xAAA9FF80
	0xFFFFFFFF
};
```


