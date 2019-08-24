# 1. DAC with sync mode
## 1.1 参考代码
https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/firmware/SAME54_DAC_sync.7z

## 1.2 START 配置界面
<br/> a.reference 选择：在A版本的器件中选择“Voltage supply”是无效的，该问题在器件D版本中已经解决。
<br/> b.如果需要输出一个静态的电压，必须设置refresh period.(注意：因为Trefesh = REFRESH * Tosculp32k, 而DAC保持1个LSB的时间为100us, 所以建议REFRESH设为2.)
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/picture_resouce/SAME54_DAC_001.png)
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/picture_resouce/SAME54_DAC_002.png)
