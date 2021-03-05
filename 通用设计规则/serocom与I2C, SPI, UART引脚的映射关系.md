# 说明：这篇文章主要说明Microchip SAM系列单片机SERCOM模块与I2C,SPI,UART的pin口映射关系。

## 1 SERCOM模块与SPI引脚的映射关系：
### 1.1 MCU引脚与SERCOM模块的引脚映射关系
![images](https://github.com/yuchengstudio/cortex-M/blob/master/%E9%80%9A%E7%94%A8%E8%AE%BE%E8%AE%A1%E8%A7%84%E5%88%99/reference/SERRCOM_SPI_001.png)

### 1.2 SERCOM模块引脚与SPI模块引脚的映射关系
![images](https://github.com/yuchengstudio/cortex-M/blob/master/%E9%80%9A%E7%94%A8%E8%AE%BE%E8%AE%A1%E8%A7%84%E5%88%99/reference/SERRCOM_SPI_002.png)

备注：以上位信息在对应模块的CTRLA寄存器中
<br/>
![images](https://github.com/yuchengstudio/cortex-M/blob/master/%E9%80%9A%E7%94%A8%E8%AE%BE%E8%AE%A1%E8%A7%84%E5%88%99/reference/SERRCOM_SPI_003.png)

<br/> 小技巧：
<br/>***1:Data In Pinout[DI] 数据输入引脚可以被映射在SERCOM_PAD[0], SERCOM_PAD[1], SERCOM_PAD[2], SERCOM_PAD[3]任意一个口***
<br/>***2:所以实际上只要确认好 DO, SCK, SS 的对应关系就好。***

## 2 SERCOM模块与I2C引脚的映射关系：与SPI同理
## 3 SERCOM模块与UART引脚的映射关系：与SPI同理

