# 参考代码
https://github.com/yuchengstudio/cortex-M/blob/master/cortex-M4/SAME54/21.RTC-%20%E5%AE%9E%E6%97%B6%E6%97%B6%E9%92%9F/reference/CAL.7z

# 调试思路
1.使用RTC做唤醒时钟源。
2.在RTC唤醒后进入Reset handler。
3.在Reset Handler后读RTC 

# note
需要在start 的RTC界面中去掉“Force reset RTC on initializtion”,这样就不会在back up 唤醒后复位RTC了，这样RTC就能正常保持时间的正常运行。
