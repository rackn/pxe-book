



UEFI vs. Legacy BIOS
=========================

Legacy BIOS is the firmware for hardware initialization during booting. The primary issue of legacy BIOS was the size constraint in. With legacy BIOS, the MBR could only handle partitions of less than two TB.

UEFI was created to solve the issue of size limits. UEFI (Unified Extensible Firmware Interface) is a specification for interface between the OS and firmware. It boots off of remote storage using network protocols that are not comprehended by legacy BIOS. It is worth noting that UEFI has become a sort of mini OS that is capable of some OS functions, but because few people have created systems for UEFI, it is not as rich as an actual OS. 

UEFI hit a stumbling block in the beginning, so instead of waiting on UEFI, other work-arounds for the BIOS size constraint were created. For example, Ubuntu can handle more than two TB by doing some partitioning tricks during installation. Now that UEFI has gotten past that block, there is a general industry move to UEFI because some systems are ending support of legacy BIOS and there are some architectures that never supported legacy BIOS to begin with. 


DRP Applications
~~~~~~~~~~~~~~~~

Digital Rebar Provision can handle multiple different install programs, and has separate boot programs for UEFI and for legacy BIOS. UEFIO runs ELILO while legacy BIOS runs PXE Linux. Both ELILO and PXE Linux process a set of configuration files to tell the machine what to boot next. They are similar in appearance and end results, but function differently.  

By default, DHCP has the bootfile image that it serves to nodes to tell the nodes how to boot. When booting DRP with legacy BIOS in the DRP quick start, use lpxelinux.0. For UEFI, boot64.eli has the program that runs in UEFI and asks ELILO for configuration.

DRP can be configured to return different files based on system architecture, which allows for a mixed system. DRP can then send the correct response to the DHCP server from the client through DRP by using parameter expansions inside option field. Get option from packet and test value. 

		{{if (eq (index . 77) “iPXE”) }}default.ipxe{{else if (eq (index . 93) “0")}}lpxelinux.0{{else}}boot x64.efi{{end}}
This string, when entered into the bootenv field, will allow DRP to detect the three default modes that it can handle.







In PXE Linux there are specifications for the kernel

Eulilo??? takes a similar set of options in a different format

Have tooling to proivde those images

By Default the DHCP has the bootfile that it serves to nodes in that it tells nodes how to boot

If always booting UEFI, put boot.x64.efi

asks for eulilo conf and not boot conf.

DRP asks for the network architecture which allows a mixed system, can send the correct response to the server from the client through DRP by looking at the parameter expansion inside option fields, get option from packet and test a value


{{if (eq (index . 77) “iPXE”) }}default.ipxe{{else if (eq (index . 93) “0")}}lpxelinux.0{{else}}bootx64.efi{{end}}

This string will let DRP detect mode
makes choices about the clients to decide their booting location