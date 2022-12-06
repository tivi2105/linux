# CMPE283-assignment-2
**In this project we will modify the CPUID emulation code in KVM to report backadditional information when special CPUID leaf nodes are requested.**

## **Steps to cpmplete this assignment**
* Install git and fork official linux repository.
* Install required packages using below comands:
    * sudo apt-get install make
    * sudo apt-get install gcc
    * sudo apt-get install libssl-dev
    * sudo apt-get install libncurses-dev
    * sudo apt-get install libelf-dev
* Clone the forked repository into local and CD into linux folder.
* Update the .config file using below command:
    * sudo cp /boot/config-5.15.0-1025-gcp .config (version may vary, use uname -a to get the kernal version).
    * Comment out **CONFIG_SYSTEM_TRUSTED_KEYS** and **CONFIG_SYSTEM_TRUSTED_KEYRING** variables, update the **CONFIG_SYSTEM_REVOCATION_KEYS** value to empty string ("").
* Execute "make oldconfig" command
* Before building the kernel, we need to make changes in vmx.c and cpuid.c files for 0xffffffc and 0xffffffd.
* Buidling kernel
    * sudo make -j 4 modules
    * sudo make -j 8
    * sudo make modules_install && sudo make install
    * sudo reboot
    * sudo lsmod | grep kvm (rsmod if any kernels are already mounted).
    * sudo modprobe kvm
    * sudo modprobe kvm_intel
* To test the kernel we created and mounted, we need to be in that kernel.
* We need virtual manager for testing.
* We need to follow steps from below mentioned websited:
    * Install ubuntu desktop - https://phoenixnap.com/kb/how-to-install-a-gui-on-ubuntu
    * Install chrome remote desktop - https://ubuntu.com/blog/launch-ubuntu-desktop-on-google-cloud
    * Wget https://releases.ubuntu.com/18.04/ubuntu-18.04.6-live-server-amd64.iso to download iso image
    * sudo apt-get install virt-manager  - to start virtual manager
* Install cpuid package.
* We need to write our own test file and run it to see the output.
