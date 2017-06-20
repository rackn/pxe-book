



Downloading the Initial Kernel
==============================

Before looking into the technical steps required to download the initial kernel, it is important to be clear on what a kernel is. The kernel is the core of any operating system. It is responsible for communication between the hardware and applications running on the computer. The kernel is primarily responsible for mediating access to the CPU, memory and devices. 

Installing a kernel on bare hardware can be a very time consuming task especially when such installs are required multiple times.
In response to this issue, PXE can be used to install a very basic kernel onto hardware. This very simple kernel is only capable enough to request an IP from the DHCP server and then to request and install a more advanced kernel through TFTP.

The second kernel is similar to the first that it must request an IP from DHCP, additionally it will only be used to request and install a final kernel using HTTP instead of the much slower TFTP. 

It should be noted that if DHCP is configured incorrectly it will assign each kernel a different IP address which will triple the number of IPs employed by the system. 