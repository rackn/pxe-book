



Downloading the Initial Kernel
==============================

Chapter 3.1 'Getting on the Network' explored the interaction between a machine and a DHCP server.  This section will look at the processes related to installing the initial kernel.  

Before looking into the technical steps required to download the initial kernel, it is important to be clear on what a kernel is.  The kernel, as the name implies, is the core of any operating system.  It is responsible for communication between the hardware and applications running on the machine.  Its primary task is to mediate access to the CPU, memory, and devices.  

Installing a kernel on bare metal can be a very labor-intensive task, especially when such installs are required across large server networks.  
In response to this issue, PXE can be used to network boot a very basic kernel onto a computer's hardware.  This kernel is only capable enough to request an IP address from the DHCP server, then request and install a more advanced kernel through TFTP.  

The second kernel is similar to the first in that it must request an IP address from the DHCP server.  Additionally, it will only be used to request and install a final kernel using HTTP, instead of the much slower TFTP.  This allows for either the install of the Sledgehammer kernel or even of a complete operating system.  

It should be noted that if DHCP is configured incorrectly it will assign both kernels and the final operating system different IP addresses which will triple the number of IP addresses employed by the subnet and waste resources.  

<Probably want a Diagram of the Kernel install>

<Probably want a run through of how this works with drp> *I will need some tech help for this part*