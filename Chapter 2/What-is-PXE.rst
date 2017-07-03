



What is PXE? A History
======================

Before diving into the origin story of PXE it is important to define it. PXE, also known as Preboot eXecution Environment is a standardized client/server environment that allows for a device to be booted from a server before an operating system has been loaded onto that device. This can be done remotely and without a hard drive. It is used in conjunction with DHCP and TFTP.

PXE originated from Intel's Wired for Management, a system that was first released in late 1998 and is now considered obsolete. WfM has been replaced by Intelligent Platform Interface Management (IPMI) for servers and Intel Active Management Technology (AMT) for personal computers. The initial goals of WfM were to lower the cost of network management and allow for remote control and management of devices in large networks. Because PXE could be booted from an external storage device, it eliminated any dependence on disk drives.

The DHCP and PXE process follows a path similar to that described in section 3.1, "Getting on the Network." The difference is the machine's DHCPDiscover package includes DHCP option 60 <ref 3.2 dhcp options> identifying the machine as PXE-enabled. After the machine has accepted a DHCPOffer, the machine will unicast a request for a bootserver and bootstrap file to the server. Refer to 2.1 "What is Bootstrapping" for further information on bootstrap file. 



