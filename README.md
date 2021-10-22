usbq and usbq-core

These are userland apps and kernel driver for sniffing and manipulating usb devices.
I havent tried them  yet as the kernel module ued deprecated set/get_fs so while
making those tiny fixes I added a kernel module param for the ip address of
usbq so recompiling the driver is no longer needed.

Tested on 5.12.19

hints; I dunno why insmod worked great for me for a very long time without an issue
but now any and all outa tree modules wont have symbols resolved when loading via
insmod. so cp it to your modules folder (I reuse/create updates/dkms), depmod, them modprobe.
example for 5.12.19

sudo mkdir -p /lib/modules/5.12.19/updates/dkms/

sudo cp ubq_core.ko /lib/modules/5.12.19/updates/dkms/

sudo depmod

sudo modprobe ubq_core ip_num=192.168.1.77

The ip address will default to 192.168.1.169 if no param is given

