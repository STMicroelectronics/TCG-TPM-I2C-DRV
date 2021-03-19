# TCG-TPM-I2C-DRV
Linux driver for I2C TPM compliant with TCG specification

This patch can be used to create a driver for an STMicroelectronics TPM withan I²C interface in a 5.4 Linux kernel.
It also improves the performance with an optimized polling during the communication with the TPM. 

## Tested with :

### Platform :
Raspberry Pi 3B+, Raspberry Pi 4B
### OS : 
Raspbian 
### Linux kernel version : 
5.4.83, downloaded from https://github.com/raspberrypi/linux
### TPM family :
[ST33TPHF20I2C](https://www.st.com/en/secure-mcus/st33tphf20i2c.html), [ST33TPHF2XI2C](https://www.st.com/en/secure-mcus/st33tphf2xi2c.html), [ST33TPHF2EI2C](https://www.st.com/en/secure-mcus/st33tphf2ei2c.html), [ST33GTPMAI2C](https://www.st.com/en/secure-mcus/st33gtpmai2c.html), [ST33GTPMII2C](https://www.st.com/en/secure-mcus/st33gtpmii2c.html)

## Patch Application

### To apply the patch
#### download Linux kernel sources
#### copy the patch into the linux/drivers/char directory
#### run from the char directory with :
patch -b -p0 < patchTPMv_5_4_2.patch


### Patch version : 5.4.2
CHANGELOG : 

#### 5.4.2 : 
- Added remove function for tpm_tis_i2c

#### 5.4.1
- Added optimisation of polling in tpm-interface.c 
- Fixed (i<0) into (i<=0) for a u32

#### 5.4.0
- Created I²C TPM Driver for kernel 5.4
