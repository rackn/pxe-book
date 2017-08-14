



UEFI vs. Legacy BIOS
=========================

Legacy BIOS is the firmware for hardware initialization during booting.  The primary issue of legacy BIOS was the size constraint, which prevented BIOS from operating on systems with large storage requirements without an excessively complex workaround.  The root of the problem is that the legacy BIOS MBR can only handle partitions of less than two terabytes, and any more will simply be inaccessible.  Fortunately, there is a simple solution available and usable through the Digital Rebar Provision.  

UEFI was created to solve the issue of partition limits.  UEFI (Unified Extensible Firmware Interface) is a specification for the interface between the OS and firmware.  It boots off of remote storage using network protocols that are not comprehended by legacy BIOS.  It is worth noting that UEFI has become a sort of mini OS that is capable of some operational functions, but because few people have created systems for UEFI, it is not as rich as an actual OS.  

While UEFI is probably the single best solution today, during development UEFI hit a stumbling block in the beginning. Instead of waiting on UEFI, other workarounds for the BIOS size constraint were created.  For example, Ubuntu can handle more than two TB by doing some partitioning tricks during installation.  Now that UEFI has gotten past that block, there is a general industry move to UEFI because some systems are ending support of legacy BIOS and there are some architectures that never supported legacy BIOS, to begin with.  


DRP Applications
~~~~~~~~~~~~~~~~

DRP can handle multiple different install programs and has separate boot programs for UEFI and for legacy BIOS.  UEFIO runs ELILO while legacy BIOS runs PXE Linux.  Both ELILO and PXE Linux process a set of configuration files to tell the machine what to boot next.  They are similar in appearance and end results but function differently.  

By default, DHCP has the bootfile image that it serves to nodes to tell the nodes how to boot. When booting DRP with legacy BIOS in the DRP quick start, use lpxelinux.0. For UEFI, boot64.eli has the program that runs in UEFI and asks ELILO for configuration.

DRP can be configured to return different files based on system architecture, which allows for a mixed system.  DRP can then send the correct response to the DHCP server from the client through DRP by using parameter expansions inside option field.  The parameter expansion first gets the option from the packet and tests a value to determine the architecture of that node, and then uses that to create the appropriate response be it configured for BIOS or UEFI. 

        {{if (eq (index . 77) “iPXE”) }}default.ipxe{{else if (eq (index . 93) “0")}}lpxelinux.0{{else}}boot x64.efi{{end}}
This string, when entered into the bootenv field, will allow DRP to detect the three default modes that it can handle.  
