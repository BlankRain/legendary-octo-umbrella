# legendary-octo-umbrella

## tools
```
https://hub.docker.com/r/joshwyant/gcc-cross/
docker pull joshwyant/gcc-cross

docker run -v $(pwd):/kernel -it joshwyant/gcc-cross bash

sudo apt-get install xorriso

wget https://download.qemu.org/qemu-3.0.0.tar.xz
tar xf qemu-3.0.0.tar.xz
cd qemu-3.0.0
./configure
make

sudo cp ./qemu-3.0.0/i386-softmmu/qemu-system-i386   /usr/bin/qemu-system-i386
```

## compile
in docker
```
i686-elf-as  boot.s -o boot.o

i686-elf-gcc -c kernel.c -o kernel.o -std=gnu99 -ffreestanding -O2 -Wall -Wextra

i686-elf-gcc -T linker.ld -o umbrella.bin -ffreestanding -O2 -nostdlib boot.o kernel.o -lgcc

```

## test

```
qemu-system-i386 -kernel myos.bin

```
## isotest
```

grub-mkrescue -o myos.iso iso

qemu-system-i386 -cdrom myos.iso
```
