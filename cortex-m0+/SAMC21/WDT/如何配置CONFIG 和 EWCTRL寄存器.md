1.如何配置WDT的CONFIG 及EWCTRL寄存器
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-m0%2B/SAMC21/WDT/reference/WDT_operation_001.png)

```
void WDT_Enable( void )
{
    /*额外添加，WDT配置*/
    /*
     * 1.WDT配置必须在WDT使能之前完成
     * 2.WDT的配置寄存器无需等待时钟同步
     */
    WDT_REGS->WDT_CONFIG |= WDT_CONFIG_PER_CYC256;
    
    WDT_REGS->WDT_CONFIG |= WDT_CONFIG_WINDOW_CYC1024;
    
    WDT_REGS->WDT_EWCTRL |= WDT_EWCTRL_EWOFFSET_CYC128;
    
    /* Checking if Always On Bit is Enabled */
    if((WDT_REGS->WDT_CTRLA & WDT_CTRLA_ALWAYSON_Msk) != WDT_CTRLA_ALWAYSON_Msk)
    {
        /* Enable Watchdog Timer */
        WDT_REGS->WDT_CTRLA |= WDT_CTRLA_ENABLE_Msk;

        /* Wait for synchronization */
        while(WDT_REGS->WDT_SYNCBUSY);
    }

    /* Enable early warning interrupt */
    WDT_REGS->WDT_INTENSET = WDT_INTENSET_EW_Msk;
}
```
