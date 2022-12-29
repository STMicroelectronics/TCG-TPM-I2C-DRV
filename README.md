# TCG-TPM-I2C-DRV
Linux driver for I2C TPM compliant with TCG specification

This patch can be used to create a driver for an STMicroelectronics TPM withan I²C interface in a 5.10 Linux kernel.
It also improves the performance with an optimized polling during the communication with the TPM. 

## Tested with :

### Platform :
Raspberry Pi 4B
### OS : 
Raspbian 
### Linux kernel version : 
5.10.110, downloaded from https://github.com/raspberrypi/linux
### TPM family :
[ST33TPHF20I2C](https://www.st.com/en/secure-mcus/st33tphf20i2c.html), [ST33TPHF2XI2C](https://www.st.com/en/secure-mcus/st33tphf2xi2c.html), [ST33TPHF2EI2C](https://www.st.com/en/secure-mcus/st33tphf2ei2c.html), [ST33GTPMAI2C](https://www.st.com/en/secure-mcus/st33gtpmai2c.html), [ST33GTPMII2C](https://www.st.com/en/secure-mcus/st33gtpmii2c.html)

## Patch Application

### To apply the patch
#### download Linux kernel sources
#### copy the patch into the linux/drivers/char directory
#### run from the char directory with :
patch -b -p0 < patchTPMv_5_10_1.patch

patch -b -p0 < 02-patchTPMv_5_10_1.patch

#### 02-patchTPMv_5_10_1.patch:
Fixed a series of issues in tpm_tis_i2c_read_bytes functions that caused when the number of bytes read exceeding 260 (limited to 0xff in this case).

1. When the number of bytes read in tpm_tis_i2c_read_bytes function exceeds 260, the read will fail, and the variable i will not increment normally, causing it to freeze in the while loop.

2. When tpm_tis_i2c_read_bytes function, the read failure returns a negative value, and the normal variable 'i' is incremented normally, after exiting while, due to the mismatch of the 'size' variable type in the tpm_tis_recv, it will cause a stack overflow when the crc_ccitt in the tpm_tis_i2c_check_data function.
### Patch version : 5.10.1
CHANGELOG : 

#### 5.10.1
- update for write 16 and write 32 access

#### 5.10.0
- Created I²C TPM Driver for kernel 5.10
