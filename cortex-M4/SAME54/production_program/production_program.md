
# 1.使用命令行erase chip
<br/>-t EDBG :使用EDBG工具
<br/>-i SWD  :使用SWD接口
<br/>-d ATSAME54P20A : 芯片为ATSAME54P20A
<br/>chiperase : 檫除芯片动作
<br/>例子： atprogram -t EDBG -i SWD -d ATSAME54P20A chiperase


# 2.使用命令行烧录程序
<br/>-t EDBG :使用EDBG工具
<br/>-i SWD  :使用SWD接口
<br/>-d ATSAME54P20A : 芯片为ATSAME54P20A
<br/>-f C:\Users\A18428\Desktop\program\SAME54_CLOCK_SWITCHING_1.hex :需要下载的程序
<br/>- --verify :程序烧写完之后做验证工作

<br/>例子： atprogram -t EDBG -i SWD -d ATSAME54P20A program -f C:\Users\A18428\Desktop\program\SAME54_CLOCK_SWITCHING_1.hex --verify
