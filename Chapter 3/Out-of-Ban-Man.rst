



What Comes Next? Out-of-Band Management - IPMI
==============================================

The next stage is the remote management of the network, which is accomplished using out-of-band management.  

Out-of-band management (OOBM) refers to a network management system that allows remote access to the devices in a network.  One example of OOBM is lights-out management (LOM), which uses a dedicated channel to manage and maintain network devices.  In this section, the goal of OOBM is to have access to a network even when the network is unavailable, such as before it is booted or during a system failure.  This requires the exclusive OOBM model, in which the OOBM system is completely isolated from the production environment. 

The goal of OOBM is accomplished with Intelligent Platform Management Interface (IPMI).  IPMI defines the interfaces used for OOBM of a network.  An OOBM system based on IPMI allows for remote maintenance of multiple, separate servers.  Because IPMI works independently of an operating system, it allows for access before booting an OS, when an OS is powered down, or after a system failure. 