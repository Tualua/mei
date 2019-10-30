# mei
Intel MEI Driver for OCP patched for newer kernels

Tested on Quanta Windmill, Ubuntu 18.04.3 with kernel 4.18.20

How to install

    sudo make install
    sudo rmmod mei_me
    sudo rmmod mei
    sudo modprobe mei
