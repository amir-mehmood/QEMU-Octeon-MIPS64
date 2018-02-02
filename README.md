 This code is enhancing QEMU capability such that it can emulate Octeon MIPS Linux Operating System and user applications.

Please use the following paper for citation in academic papers.

M. A. Mehmood, Q. U. Ain, A. Akram, A. Qadeer and A. Waheed, "Emulating an Octeon MIPS64 based embedded system on X86 in QEMU," 2016 19th International Multi-Topic Conference (INMIC), Islamabad, 2016, pp. 1-7


# QEMU-Octeon-MIPS64
Patch for the emulation of Octeon MIPS64 in QEMU

Preparing HOST
==============
- Download qemu-1.0.1 tar
- cd and run
	export CFLAGS='-lm -lrt'
	./configure --target-list=mips64-softmmu
	make
- copy patch to qemu-1.0.1 top directory
	patch -p1 > host.patch
	make
- modified Qemu binary "qemu-system-mips64" is found in qemu-1.0.1/mips64-softmmu 

 Preapring GUEST
================
Note: Download GUEST.patch from the following link:

https://drive.google.com/file/d/1vRYhKqbuCpcIWCWVgAhDqai6KhsLTE-o/view?usp=drive_web

- OCTEON-SDK-2.0.0
- extarct & apply the guest.patch
- make the kernel


To Run single Core version:
============================

./qemu-system-mips64 -m 256 -M octeon -nographic -bios <oath to binary>/u-boot-octeon_ebh5610.bin -kernel <path to binary>/vmlinux.64 -append 'coremask=0xfff mem=0 root=/dev/sda2'

when uboot command promt occur:

Octeon ebh5610# bootoctlinux
