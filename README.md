# TCG-TPM-I2C-DRV
Linux driver for I2C TPM compliant with TCG specification
I2C TPM driver is natively in linux kernel since 6.1.
We provide overlay file to simplify TPM activation.

## Advising
Select branch 5.4.y and 5.10.y, for your legacy linux branch to integrate a driver for an STMicroelectronics TPM with an I²C interface.

## TPM activation by overlay file

directly after flash your sd card :
### Copy tpm-stm.dtbo file in "overlays" directory 
### merge or modify config.txt
#### remove  # on (to activate SPI and I2C bus)
dtparam=i2c_arm=on

dtparam=spi=on
#### add (to activate I2C and SPI TPM driver)
dtoverlay=tpm-stm

### Tested with :

#### Platform :
Raspberry Pi 3B+, Raspberry Pi 4B, Raspberry Pi 5
#### OS : 
Raspbian 
#### Linux kernel version : 
6.1 , downloaded from https://github.com/raspberrypi/linux

#### TPM family :
[ST33TPHF20I2C](https://www.st.com/en/secure-mcus/st33tphf20i2c.html), [ST33TPHF2XI2C](https://www.st.com/en/secure-mcus/st33tphf2xi2c.html), [ST33TPHF2EI2C](https://www.st.com/en/secure-mcus/st33tphf2ei2c.html), [ST33GTPMAI2C](https://www.st.com/en/secure-mcus/st33gtpmai2c.html), [ST33GTPMII2C](https://www.st.com/en/secure-mcus/st33gtpmii2c.html)

## STM32M1xx-DK platform
To integrate I2C or SPI TPM on
- [STM32MP157F-DK2](https://www.st.com/en/evaluation-tools/stm32mp157f-dk2.html) board.
- [STM32MP135F-DK](https://www.st.com/en/evaluation-tools/stm32mp135f-dk.html) board.
  
please go to dedicated github :
[STM32M1xx-DK TPM integration](https://github.com/STMicroelectronics/meta-st-x-linux-tpm)

**The main documentation linked with this X-LINUX package is available on [X-LINUX-TPM wiki article](https://wiki.st.com/stm32mpu/wiki/X-LINUX-TPM_expansion_package).**


