## Lab 06

- Name: Alec Porter
- Email: porter.223@wright.edu

## System Discovery

1. CPU info:
    - CPU brand: AMD Ryzen 9 4900HS
    - Number of cores: 8
    - Number of logical cores: 16
2. GPU info:
    - Integrated GPU info: Advanced Micro Devices, Inc. [AMD/ATI] Renoir (rev c5)
    - Dedicated GPU info: VGA compatible controller: NVIDIA Corporation TU106M [GeForce RTX 2060 Max-Q] (rev a1)
    - Link to driver software for GPU: https://www.amd.com/en/support/linux-drivers, https://www.nvidia.com/download/index.aspx
3. Memory info:
    - Physical memory (RAM) size (in GB): 15Gi (16GB)
    - Virtual memory size (in GB): 15775740 (16GB)
4. Storage info (repeat for each disk attached to your system): 
    - Disk 1 type: nvme
    - Disk 1 manufacturer and model: Sabrent
    - Total disk 1 size (in GB): 1.9T (1900G)
5. Primary partition info:
    - Primary partition mount point: /
    - Remaining space on primary partition (in GB): 861G
    - Filesystem on primary partition: ext4
6. BIOS / UEFI info: 
    - BIOS or UEFI version: GA401IV.222
    - How to access your BIOS / UEFI: frantically hit delete right after the laptop is powered on or reset
7. Kernel / OS info:
    - Bootloader software on your system: GRUB
    - Kernel version of your operating system: Linux 6.6.10-76060610-generic x86_64
    - Operating System name & version: Pop! OS 22.04 LTS, based on ubuntu debian 


## Part 2 - Virtualize the Machine

1. Virtual Machine Manager: 
    - Software & version: VirtualBox 7.0
    - Link to software URL: I used the built in gui software repository (POP! Shop) which not only installed the VM software but will notify me of updates. (https://www.virtualbox.org/) 
    - ![screenshot of installed & running software](https://github.com/WSU-kduncan/ceg2350s24-alec-porter/blob/main/Lab06/screenshot1.jpg)

2. Guest OS information: 
    - Linux distribution selected:  Pop! OS
    - URL downloaded from: https://pop.system76.com/

3. Guest VM resource allocations: 
    - Number of Virtual CPUs: 4
    - RAM: 4096MB
    - Hard disk space: 25GB 

4. Guest OS Installation:
    - Note steps completed to install and then run the guest operating system:
	-- Selected new in Virtual Box, selected ISO, defined memory/cpu/drive sizes then hit start. 
	-- Pop OS starts up in a virtual session and automatically starts the installer once booted into the live session
	-- Selected clean install and the virtual drive created by Virtual Box.
	-- The rest of the installation is just like installing Pop! OS on bare metal hardware (set user name/password, etc.)
    - ![screenshot of installed & running Guest OS in VM](https://github.com/WSU-kduncan/ceg2350s24-alec-porter/blob/main/Lab06/screenshot.jpg)

## Part 3 - Virtual Playground:

1. How to change your desktop background in your VM: Right click on the desktop, select change backgroud, select the background you want to use.
2. How to install VSCode in your VM: Use the Pop! Shop and seach for Visual Studio Code.  It's available in the repository and you can install it from there.
3. How to connect to your AWS instance from your VM using `ssh`: logged into AWS Academy and downloaded the .pem file, changed the permission on the .pem file (chmod 600), use the ssh command: ssh -i ~/Downloads/labsuser.pem ubuntu@34.225.112.222.  Then created a config file in the .ssh folder for easier login.
- ![screenshot 1](https://github.com/WSU-kduncan/ceg2350s24-alec-porter/blob/main/Lab06/screenshot2.jpg) 
