---
title: "Running Windows XP on Ubuntu with KVM"
date: 2024-02-06
categories: [Running Windows XP on Ubuntu with KVM]
tags: [running windows xp on ubuntu with kvm]  # TAG names should always be lowercase
---


Hey there, welcome back to "Adnane's World"! It's been ages since I hit you with some wisdom, but guess what? I survived my final exams (next semester is one day away :/ ). Today, we're jumping into the exciting world of KVM (Kernel-based Virtual Machine) and virtualization.

Let's do something cool together! I'll show you how to use KVM to run Windows XP on your Ubuntu. It's like blending vintage Windows with Ubuntu. Easy and fun! Let's get started!

<h4><b>Ubuntu Update</b></h4> 
To start, launch the terminal and update your local package index as follows.

![Desktop View](/assets/img/s1.png){: width="250" height="100" }     

<h4><b>Check Virtualization Status</b></h4>
Before proceeding, check if virtualization is enabled on your system. Your CPU must support KVM virtualization, which requires an Intel VT-x (vmx) or AMD-V (svm) processor. Run the following command, and if the output is greater than 0, virtualization is enabled. Otherwise, it's disabled, and you need to enable it.

![Desktop View](/assets/img/egrep.png){: width="500" height="300" }              

![Desktop View](/assets/img/11.png){: width="600" height="200" }

If virtualization is not enabled, activate it in your system's BIOS settings. Additionally, check KVM virtualization status with the following command:

![Desktop View](/assets/img/s3.png){: width="180" height="100" }  

For this to work, you need to have the cpu-checker package installed. If not, install it:

![Desktop View](/assets/img/s4.png){: width="400" height="200" }  

![Desktop View](/assets/img/12.png){: width="600" height="200" }

Then run the kvm-ok command. If KVM virtualization is enabled, you should get the following output:

![Desktop View](/assets/img/s3.png){: width="180" height="100" }  

![Desktop View](/assets/img/13.png){: width="600" height="200" }

<h4><b>Install KVM on Ubuntu</b></h4> 
Next, run the following command to install KVM and additional virtualization packages on Ubuntu, in my case iuse Ubuntu Lite :

![Desktop View](/assets/img/s5.png){: width="800" height="800" }  

![Desktop View](/assets/img/14.png){: width="600" height="200" }

<h4>Breakdown of installed packages:</h4>
    qemu-kvm: Open-source emulator and virtualization package providing hardware emulation.
    virt-manager: Qt-based graphical interface for managing virtual machines through the libvirt daemon.
    libvirt-daemon-system: Package providing configuration files required to run the libvirt daemon.
    Virtinst: Set of command-line utilities for provisioning and modifying virtual machines.
    libvirt-clients: A set of client-side libraries and APIs to manage and control virtual machines and hypervisors from the command line.
    bridge-utils: Set of tools for creating and managing bridge devices.

<h4><b>Enable Virtualization Daemon (libvirtd)</b></h4>
With all packages installed, activate and start the Libvirt daemon.

![Desktop View](/assets/img/s6.png){: width="500" height="200" }  

Check that the virtualization daemon is running:

![Desktop View](/assets/img/s7.png){: width="500" height="200" }  

![Desktop View](/assets/img/15.png){: width="600" height="200" }

Additionally, add the currently logged-in user to the kvm and libvirt groups to create and manage virtual machines.

![Desktop View](/assets/img/s8.png){: width="500" height="200" }  

The $USER environment variable points to the currently logged-in user. To apply this change, you need to log out and log back in.

<h4><b>Launch KVM Virtual Machines Manager</b></h4>
Once KVM is installed, start creating virtual machines using the virt-manager graphical interface. Use the GNOME search utility and look for "Virtual Machine Manager".
Click on the appearing icon to launch the Virtual Machine Manager interface.

![Desktop View](/assets/img/16.png){: width="600" height="200" }
![Desktop View](/assets/img/17.png){: width="600" height="200" }

Click on "File" and then select "New Virtual Machine." Alternatively, use the displayed button

![Desktop View](/assets/img/18.png){: width="600" height="200" }

This opens the virtual machine installation wizard, presenting four options:
        Local installation media (ISO or CDROM image)
        Network installation (HTTP, HTTPS, and FTP)
        Import an existing disk image
        Manual installation
In this guide, assuming you have downloaded a Windows XP ISO image ( you can download the ISO file from archive.org ), select the first option and click 'Forward.'

![Desktop View](/assets/img/19.png){: width="600" height="200" }

In the next step, click 'Browse' to locate the ISO image.

![Desktop View](/assets/img/110.png){: width="600" height="200" }

In the following window, click 'Local Browse' to select the ISO image from your Linux PC's local directories.

![Desktop View](/assets/img/112.png){: width="600" height="200" }

As demonstrated below, we selected the Windows XP ISO image. Then click "Open".
Once the ISO image is selected, click 'Choose Volume' to proceed to the next step.

![Desktop View](/assets/img/113.png){: width="600" height="200" }

Next, set the RAM and the number of CPU cores for your virtual machine and click "Forward".

![Desktop View](/assets/img/114.png){: width="600" height="200" }

In the following step, set the disk space for your virtual machine and click "Forward".

![Desktop View](/assets/img/115.png){: width="600" height="200" }

Finally, click 'Forward' to complete the virtual machine configuration.

![Desktop View](/assets/img/116.png){: width="600" height="200" }

Shortly after, the virtual machine creation process will start.

Once finished, the virtual machine will boot with the operating system installation program displayed.
From there, you can proceed with installing your preferred system.

![Desktop View](/assets/img/117.png){: width="700" height="300" }

