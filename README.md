# Linux_Kernel
Required : Toolchain,Emulator,Rootfs,Kernel Image, Dtb file
1. Install linaro toolchain from ubuntu package manager
 --> sudo apt install gcc-arm-linux-gnueabi
 
2. Setting up Qemu
 --> sudo apt-get install qemu-system-arm
 
3. Prebuilt Yocto Image (Download core-image-minimal-qemuarm.ext4 (pre-built rootfs generated from Yocto project)
from this link,rename it as rootfs.img)
 --> downloads.yoctoproject.org/releases/yocto/yocto-2.5/machines/qemu/qemuarm/
(You may need to resize rootfs.img
e2fsck -f rootfs.img            # sudo
resize2fs rootfs.img 16M        # sudo )
All the steps in 3. are done and saved as rootfs.img in the directory.

4. Pre-built kernel image and dtb file are avialable in the directory.

5. SD_card Approach: run the below command in terminal.
qemu-system-arm -M vexpress-a9 -m 1024 -serial stdio \
-kernel zImage -dtb vexpress-v2p-ca9.dtb \
-sd rootfs.img -append "console=ttyAMA0 root=/dev/mmcblk0 rw"

Login: root.

 
