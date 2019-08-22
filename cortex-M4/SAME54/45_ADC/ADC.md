# 1.使用START配置一个基本的ADC工程：
## 1.1工程演示目标：使用“software trigger”触发ADC转换，并将转换数据通过EDBG串口发送到terminal终端。
### 1.1.1 根据需要的Pin口配置ADC模块采样通道(比如我们这里需要使用PB04作为模拟采样输入)
在datasheet中找到PB04对应ADC模块的ADC1/AIN[6] (即：PB04对应ADC1的输入通道6)
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/picture_resouce/SAME54_ADC_001.png)

根据datasheet的信息，在相应START的ADC模块配置如下：
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/picture_resouce/SAME54_ADC_002.png)
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/picture_resouce/SAME54_ADC_003.png)

### 1.1.2 根据需要配置ADC（分辨率、参考源、差分or单端... ）
此部分内容根据实际项目需求选择
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/picture_resouce/SAME54_ADC_004.png)
