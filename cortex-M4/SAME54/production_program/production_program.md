
1.使用命令行erase chip
-t EDBG :使用EDBG工具
-i SWD  :使用SWD接口
-d ATSAME54P20A : 芯片为ATSAME54P20A
chiperase : 檫除芯片动作
  atprogram -t EDBG -i SWD -d ATSAME54P20A chiperase
