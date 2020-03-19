# 在应用中添加如图所示的代码
先读出fuse位，然后根据实际需要开启的fuse位，只改确认需要改的位，然后再写入。
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/production_program/reference/fuse_004.png)
```
/* Demo code for fuse setting with APIs */
#if 1
	/* Read fuse */
	user_fuse_read((uint32_t *)&fuse_buf);

	/* Update fuse if needed */
	if ( (fuse_buf.bit.BOD33_DIS != CFG_BOD33_DIS) || (fuse_buf.bit.BOD33_ACTION != CFG_BOD33_ACTION) ||
		 (fuse_buf.bit.WDT_ENABLE != CFG_WDT_ENABLE) || (fuse_buf.bit.WDT_PER != CFG_WDT_PER)
	   ) {
		fuse_buf.bit.BOD33_DIS = CFG_BOD33_DIS;
		fuse_buf.bit.BOD33_ACTION = CFG_BOD33_ACTION;

		fuse_buf.bit.WDT_ENABLE = CFG_WDT_ENABLE;
		fuse_buf.bit.WDT_PER = CFG_WDT_PER;

		/* Write fuse */
		user_fuse_write((uint32_t *)&fuse_buf);

		/* Reset system to reload fuse */
		NVIC_SystemReset();
	}
#endif
```
