
# 1.使用命令行erase chip
<br/>-t EDBG :使用EDBG工具
<br/>-i SWD  :使用SWD接口
<br/>-d ATSAME54P20A : 芯片为ATSAME54P20A
<br/>chiperase : 檫除芯片动作
<br/>例子： atprogram -t EDBG -i SWD -d ATSAME54P20A chiperase


# 2.编程命令使用
================================================= a 烧写程序======================================================================
<br/>-t EDBG :使用EDBG工具
<br/>-i SWD  :使用SWD接口
<br/>-d ATSAME54P20A : 芯片为ATSAME54P20A
<br/>-f C:\Users\A18428\Desktop\program\SAME54_CLOCK_SWITCHING_1.hex :需要下载的程序
<br/>- --verify :程序烧写完之后做验证工作

<br/>例子： atprogram -t EDBG -i SWD -d ATSAME54P20A program -f C:\Users\A18428\Desktop\program\SAME54_CLOCK_SWITCHING_1.hex --verify


================================================= b 烧写fuse文件===================================================================
1.先获取fuse 文件
2.使用编程命令烧写fuse 文件
<br/>-t EDBG :使用EDBG工具
<br/>-i SWD  :使用SWD接口
<br/>-d ATSAME54P20A : 芯片为ATSAME54P20A
<br/>-f -f C:\Users\A18428\Desktop\program\same54_fuse.bin :需要下载的程序
<br/>-o 0x804000 :fuse位对应的映射空间
<br/>- --verify :程序烧写完之后做验证工作

C:\Users\A18428\Documents>atprogram -t edbg -i swd -d atsame54p20a program -fs -f C:\Users\A18428\Desktop\program\same54_fuse.bin -o 0x804000 --verify

# 3.存储器写命令使用（最常用到的是fuse位烧写）

<br/> -v :烧写完后验证
<br/>-t EDBG :使用EDBG工具
<br/>-i SWD  :使用SWD接口
<br/>-d ATSAME54P20A : 芯片为ATSAME54P20A
<br/> write:写数据
<br/> -fs :写fuse 位
<br/> -- values 3992ffff : 要写入的数据（注意地址顺序，请仔细核对fuse位的高低次序）
<br/> -- offset 0x804000 : fuse位的对应的映射地址
<br/>atprogram -t EDBG -i SWD -d ATSAME54P20A write -fs --values 3992ffff --offset 0x804000


# 4.读取熔丝位信息
<br/>-t EDBG :使用EDBG工具
<br/>-i SWD  :使用SWD接口
<br/>-d ATSAME54P20A : 芯片为ATSAME54P20A
<br/> read:读
<br/> -- o 0x804000 : 要读取的内存读取地址
<br/> - s 32 读取32个字节数据
<br/>example:  atprogram -t edbg -i swd -d atsame54p20a read -o 0x804000 -s 32
