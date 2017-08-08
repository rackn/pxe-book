



What is Bootstrapping?
======================

<<<<<<< HEAD
"Bootstrapping" as a term for computing that emerged in the 1950's.  Once an initial program, typically the BIOS, is started, the computer boots itself through a series of increasingly complex and intensive programs that serve to start up the goal program which is the most complex.  This goes on until the computer is fully booted, having, following the adage, "pulled itself up by its bootstraps."  The initial program, often referred to as BIOS, is stored as firmware, usually in ROM.

The BIOS initializes memory, starts CPUs, and enables access to I/O (Input/Output) devices, such as disks or network cards.  The BIOS then searches for additional programs to load.  This next program is usually called a "boot loader" or "bootstrap loader."  The bootstrap loader resides in the MBR (Master Boot Record) on the hard drive and knows how to read the disk to look for the next part of the Operating System, a kernel (to use the linux term).  After finding a kernel the bootstrap loader goes through the process needed to load the kernel.  After successfully loading the kernel searches for, initializes, and tests other programs needed to complete the operating system start-up.
=======
"Bootstrapping" as a term for computing emerged in the 1950's.  Once an initial program, typically the BIOS, is started, the computer boots itself through a series of increasingly complex and intensive programs that serve to start up the goal program, which is the most complex.  This goes on until the computer is fully booted, having, following the adage, "pulled itself up by its bootstraps." The BIOS is stored as firmware, usually in a ROM.

The BIOS initializes memory, starts CPUs, and enables access to I/O (Input/Output) devices, such as disks or network cards.  The BIOS then searches for additional programs to load.  This next program is usually called a "boot loader" or "bootstrap loader."  The bootstrap loader resides in the MBR (Master Boot Record) on the hard drive and knows how to read the disk to look for the next part of the OS: a kernel (to use the linux term).  The kernel searches for, initializes, and tests other programs needed to complete the operating system start-up.
>>>>>>> origin/Final-Reviews

There is also bootstrapping specific to nodes.  These bootstrapping nodes, also known as rendezvous hosts, give configuration information to new nodes in the network to help them join.  A rendezvous host makes it so the user does not need people to initialize each new node.  A new node needs configuration information or else it will not be able to join the network and communicate with other nodes.  These bootstrapping-specific nodes are usually defined by their services. Some examples include RARP, BOOTP, DHCP, TFTP, HTTP, IPv6 Autoconf, and NDP.

When applied to nodes, bootstrapping refers to a similar progression wherein increasingly high capacity methods for data transfer are employed after being enabled by programs installed on the previous data transfer method.  

Within Digital Rebar, Sledgehammer is a bootstrapping tool used to perform initial node discovery and the register the nodes discovered state within the Digital Rebar node provisioning framework. 