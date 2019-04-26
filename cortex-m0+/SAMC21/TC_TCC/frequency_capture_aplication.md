# 参考文献
<br/>https://github.com/yuchengstudio/cortex-M/blob/master/cortex-m0%2B/SAMC21/TC_TCC/reference/Atmel-42454-Advanced-Features-of-SAM-D21-Timer-Counter-for-Control-Applications_Application-Note_AT12031.pdf

<br/>网络参考https://martinvb.com/wp/as5030-magnetic-encoder-capturing-a-pwm-signal-with-an-atsamd21/


# 使用TC的frequency period capture 功能
## 功能实现逻辑框图
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-m0%2B/SAMC21/TC_TCC/reference/atsamd21_capture_diagram-1.png)
<br/>note: External Interrupt (EIC) peripheral to generate an event in the internal Event System (EVSYS), 

## Period and Pulse-Width (PPW) Capture Action 工作原理
![image](https://github.com/yuchengstudio/cortex-M/blob/master/cortex-m0%2B/SAMC21/TC_TCC/reference/capture_aplication_001.png)

