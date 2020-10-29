The security bit is read by the hardware only after a reset.

After setting the fuse bit using SSB command, you can do software reset by the API NVIC_SystemReset() which resets the MCU.


The below code will set security bit and give software reset. After device reset, it turns on PB30 pin(You can choose any pin according to your custom board).

```
int main(void)

{

/* initialize PB30 as output pin */

PORT->Group[1].OUTSET.reg = PORT_PB30;

PORT->Group[1].DIRSET.reg = PORT_PB30;

/* if security bit is set */

if(NVMCTRL->STATUS.bit.SB==1) 

  {   

     /* PB30 ON */   

     PORT->Group[1].OUTCLR.reg = PORT_PB30;

  }

else

   {

     /* set security bit */

     NVMCTRL->CTRLA.reg = NVMCTRL_CTRLA_CMD_SSB | NVMCTRL_CTRLA_CMDEX_KEY;

     while(NVMCTRL->INTFLAG.reg & NVMCTRL_INTFLAG_READY == 0);

    /* reset the device */

     NVIC_SystemReset();

  }

while(1);

}
```
