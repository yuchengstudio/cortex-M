# 1.使用OSCULP32K的时钟注意事项
## 1.1在芯片初始化的时候会自动加载出厂校验值，不需要额外处理
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/21.RTC-%20%E5%AE%9E%E6%97%B6%E6%97%B6%E9%92%9F/reference/OSCULP32K_calibration.png)

<br/>注意事项
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/21.RTC-%20%E5%AE%9E%E6%97%B6%E6%97%B6%E9%92%9F/reference/OSCULP32K_CLOCK_CONFIGURATION_001.PNG)



# 2.使用外部32k的有效程序
https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/21.RTC-%20%E5%AE%9E%E6%97%B6%E6%97%B6%E9%92%9F/reference/SAME54_RTC_TEST.7z

<br/>注意事项
<br/>1.XOSC32k的1khz输出功能必须打开
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/21.RTC-%20%E5%AE%9E%E6%97%B6%E6%97%B6%E9%92%9F/reference/XOSC_CLOCK_CONFIGURATION_001.PNG)

<br/>2.Calendar模块自己的预分频必须选对，以保证喂给Calendar模块的tick是1HZ, 否则Calendar的RTC运行不正确。
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/21.RTC-%20%E5%AE%9E%E6%97%B6%E6%97%B6%E9%92%9F/reference/XOSC_CLOCK_CONFIGURATION_002.PNG)



