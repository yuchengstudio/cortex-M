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

# 步骤3
使用命令行工具烧写编译生成的hex文件。
<br/>说明：
<br/>1.不能使用atmel studio界面烧写，因为有1M的空间限制。
<br/>2.不能使用.bin文件，因为bin文件没有地址信息。



