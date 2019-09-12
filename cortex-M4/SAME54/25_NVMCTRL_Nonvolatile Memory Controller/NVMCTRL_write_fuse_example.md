# 可以使用如下参考代码，在程序里修改fuse位
``` c
//read_fuse_bits(samd51_old_fusebits);
/* Save current value of reserved fusebits */
volatile uint32_t samd51_new_fusebits[0] = samd51_modified_fusebits[0];
volatile uint32_t samd51_new_fusebits[1] = samd51_modified_fusebits[1];

void program_fuse_bits(void)
{
	/* Auxiliary space cannot be accessed if the security bit（NVMCTRL_CTRLB_CMD_SSB） is set */
	if (NVMCTRL->CTRLB.reg & NVMCTRL_CTRLB_CMD_SSB) {
		return;
	}
	/* Disable Cache */
	//temp = NVMCTRL->CTRLA.reg;
	NVMCTRL->CTRLA.reg = NVMCTRL_CTRLA_CACHEDIS0_Pos| NVMCTRL_CTRLA_CACHEDIS1_Pos;
	
	/* disable NVM operation interrupt */
	NVMCTRL->INTENCLR.reg |= NVMCTRL_INTENCLR_MASK;
	
	/* Set the NVM first address to be accessed（NVMCRL_USER = 0x00804000 in SAMD51）, command will be issued elsewhere */
	NVMCTRL->ADDR.reg = NVMCTRL_USER;
	
	
	/* Erase the user page */
	/*1.NVMCTRL_CTRLB_CMD_EP mean Erase Page - Only supported in the User page in the auxiliary space.*/
	/*2.this bit group should be written with the key value 0xA5 to enable the command written to CMD*/
	NVMCTRL->CTRLB.reg = NVMCTRL_CTRLB_CMD_EP | NVMCTRL_CTRLB_CMDEX_KEY;
	/* Wait for NVM command to complete */
	while (!(NVMCTRL->STATUS.reg & NVMCTRL_STATUS_READY));
	
	
	/* Clear error flags */
	NVMCTRL->INTENCLR.reg |= NVMCTRL_INTENCLR_MASK;
	/* Set address, command will be issued elsewhere */
	NVMCTRL->ADDR.reg = NVMCTRL_USER;
	/* Erase the page buffer before buffering new data */
	/*1.NVMCTRL_CTRLB_CMD_PBC mean Page Buffer Clear - Clears the page buffer.*/
	/*2.this bit group should be written with the key value 0xA5 to enable the command written to CMD*/
	NVMCTRL->CTRLB.reg = NVMCTRL_CTRLB_CMD_PBC | NVMCTRL_CTRLB_CMDEX_KEY;
	/* Wait for NVM command to complete */
	while (!(NVMCTRL->STATUS.reg & NVMCTRL_STATUS_READY));
	
	
	/* Clear error flags */
	NVMCTRL->INTENCLR.reg |= NVMCTRL_INTENCLR_MASK;
	/* Set address, command will be issued elsewhere */
	NVMCTRL->ADDR.reg = NVMCTRL_USER;
	/*注意用户页写入模式 */
	/*1.NVMCTRL_CTRLB_CMD_WQW mean Write Quad Word - Writes a 128-bit word at the location addressed by the ADDR register. more detail opteration mode, please refer to NVMCTRL register*/
	/*2.this bit group should be written with the key value 0xA5 to enable the command written to CMD*/
	*((uint32_t *)NVMCTRL_USER) = samd51_new_fusebits[0];
	*(((uint32_t *)NVMCTRL_USER) + 1) = samd51_new_fusebits[1];
	NVMCTRL->CTRLB.reg = NVMCTRL_CTRLB_CMD_WQW|NVMCTRL_CTRLB_CMDEX_KEY;
	/* Wait for NVM command to complete */
	while (!(NVMCTRL->STATUS.reg & NVMCTRL_STATUS_READY));
	
	
	/* Clear error flags */
	NVMCTRL->INTENCLR.reg |= NVMCTRL_INTENCLR_MASK;
	/* Set address, command will be issued elsewhere */
	NVMCTRL->ADDR.reg = NVMCTRL_USER;
	/* NVMCTRL_CTRLB_CMD_SSB: SET security bit */
	NVMCTRL->CTRLB.reg = NVMCTRL_CTRLB_CMD_SSB | NVMCTRL_CTRLB_CMDEX_KEY;
	while (!(NVMCTRL->INTFLAG.reg & NVMCTRL_INTFLAG_DONE));
	/* Restore the settings */
	/* Wait for NVM command to complete */
	//NVMCTRL->CTRLA.reg = temp;
	
	NVIC_SystemReset();//防止程序出错  考虑这里加系统复位
}

```
