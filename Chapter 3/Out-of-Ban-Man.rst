



What Comes Next? Out-of-Band Management - IPMI
==============================================

What comes next is remote management of the network, which is accomplished using out-of-band management. 

Out-of-band management (OOBM) refers to a system of network management that allows remote access to the devices in a network. One example of OOBM is lights-out management (LOM), which uses a dedicated channel to manage and maintain network devices. The goal of OOBM in this section is to have access to a network even when it is unavailable, such as before it is booted or during a system failure. 

There are two types of OOBM models: exclusive and hybrid. Exclusive OOBM means the out-of-band system is 100% isolated from the production environment. Hybrid OOBM means out-of-band system and in-band system characteristics are combined. The hybrid OOBM model is more common and less expensive, but the focus of this section is on the exclusive OOBM model because it allows for control during a network outage. 

The goal of OOBM is accomplished with Intelligent Platform Management Interface (IPMI). IPMI defines the interfaces used for OOBM of a network. An OOBM system based on IPMI allows for remote maintenance of multiple, separate servers. Because IPMI works independently of an operating system, it allows for access before booting an OS, when an OS is powered down, and after a system failure. 

*Add a section about hybrid OOBM if it is more common*