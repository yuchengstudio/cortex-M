# 1.使用START配置一个基本的ADC工程：
## 1.1工程演示目标：使用“software trigger”触发ADC转换，并将转换数据通过EDBG串口发送到terminal终端。
### 1.1.1 根据需要的Pin口配置ADC模块采样通道(比如我们这里需要使用PB04作为模拟采样输入)
在datasheet中找到PB04对应ADC模块的ADC1/AIN[6] (即：PB04对应ADC1的输入通道6)
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/picture_resouce/SAME54_ADC_001.png)

根据datasheet的信息，在相应START的ADC模块配置如下：
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/picture_resouce/SAME54_ADC_002.png)
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/picture_resouce/SAME54_ADC_003.png)

### 1.1.2 根据需要配置ADC（分辨率、参考源、差分or单端... ）
此部分内容根据实际项目需求选择（此配置中使用了外部参考A,所以在实际测试中需要在对应external refA引脚连接参考源）
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/picture_resouce/SAME54_ADC_004.png)


### 1.1.3 在应用代码中调整ADC采样通道
<br/>说明：根据1.1.2的配置，在start配置中只能启用一个通道，如果需要多通道采样，一种办法就是在应用软件中使用API函数切换采样通道
<br/>a.对应的通道选择寄存器的意思参考如下图：
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/picture_resouce/SAME54_ADC_005.png)
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/picture_resouce/SAME54_ADC_006.png)
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/picture_resouce/SAME54_ADC_007.png)

<br/>b.相应的API函数为：adc_sync_set_inputs()
<br/>函数的说明参考链接：http://atmel-studio-doc.s3-website-us-east-1.amazonaws.com/webhelp/GUID-2A8AADED-413E-4021-AF0C-D99E61B8160D-en-US-3/index.html?GUID-23D99B59-B5EA-4187-A2C7-660DE4BEE77B
```
adc_sync_set_inputs

Set ADC input source of a channel.

int32_t adc_sync_set_inputs(
    struct adc_sync_descriptor *const descr,
    const adc_pos_input_t pos_input,
    const adc_neg_input_t neg_input,
    const uint8_t channel
)

This function sets ADC positive and negative input sources.
Parameters

descr

    Type: struct adc_sync_descriptor Struct *const

    The pointer to the ADC descriptor
pos_input

    Type: const adc_pos_input_t

    A positive input source to set
neg_input

    Type: const adc_neg_input_t

    A negative input source to set
channel

    Type: const uint8_t

    Channel number


```


