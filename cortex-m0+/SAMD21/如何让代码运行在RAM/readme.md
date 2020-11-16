# 参考代码
https://github.com/yuchengstudio/cortex-M/blob/master/cortex-m0%2B/SAMD21/%E5%A6%82%E4%BD%95%E8%AE%A9%E4%BB%A3%E7%A0%81%E8%BF%90%E8%A1%8C%E5%9C%A8RAM/reference/samd21_code_in_ram_keil-20201113.7z

```
attached a SAMD21 POC example of executing code from RAM with Keil.
It demonstrates executing code from RAM with interrupt supported. SysTick interrupt will still work while doing flash programming.
The basic idea is to put vector table and related interrupt handler functions in RAM, so this ram function can still run while programming flash.

Main modified files are:
    * sam_d21_xpro.sct
    * startup_keil.c
* interrupts.c
* main.c

Result (console, 115200 baudrate):
==== Example of executing Code from RAM ====
  - Vector table (VTOR) is put in RAM
  - SysTick_Handler is put in RAM

---- Execute flash erase from RAM ----
Flash wait count during flash row erase: 1824
Start / End tick of flash row erase: 364 / 446 ticks! Tick delta = 82

---- Execute flash erase from Flash ----
Flash wait count during flash row erase: 0
Start / End tick of flash row erase: 1856 / 1858 ticks! Tick delta = 2

---- Execute flash page write ----
Flash wait count during flash page write: 622
Start / End tick of flash page write: 3203 / 3232 ticks! Tick delta = 29
```
