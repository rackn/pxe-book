



UEFI vs. Traditional BIOS
=========================


Define UEFI vs legacy BIOS
~~

UEFI= specification for interface between OS and firmware.
BIOS= firmware for hardware initialization during booting.

UEFI doesn't have 2TB size constraint of BIOS

Stuff
~~

The primary issue of legacy BIOS that UEFI solves is the size constraint in BIOS. Legacy BIOS cannot handle a disk size larger than two TB. UEFI boots off of remote storage using network protocols that are not comprehended by legacy BIOS. UEFI has become a mini operating system or sorts that is capable of some OS functions but because few people have create systems for UEFI it is not as rich as actual OS's. 
Because UEFI had issues initially, other work-arounds for the BIOS size constraint were created. For example, Ubuntu can handle more than two TB by doing some partitioning tricks during installation. There is a general industry move to UEFI because some systems are ending support of legacy BIOS and there are some architectures that never supported legacy BIOS to begin with. 

DRP Applications
~~~
Digital Rebar Provision can handle multiple different install programs, and has separate boot programs for UEFI and for legacy BIOS. UEFIO runs ELILO while legacy BIOS runs PXE. Both ELILO and PXE process a set of configuration files to tell the machine what to boot next. They appear similar, have similar end results, but function differently.  

Linux vs elilo in terms of booting. Have tooling to provide images. 



By default, DHCP has the bootfile image that it serves to nodes to tell the nodes how to boot. When booting DRP with legacy BIOS in the quickstart, use lpxelinux.0. For UEFI, boot64.eli has the program that runs in UEFI. ask ELILO for confirmation



Need to use both. Drp client can configured to return diff files based on sys architecture. By booting chooser into bootenv file, lets user pick which boot file to use based on architecture. Param expansions inside option field. Get option from packet and test value. 

Put (string) into bootenv field will allow to detect modes. Detects 3 defaults that drp can handle. 
{{if (eq (index . 77) “iPXE”) }}default.ipxe{{else if (eq (index . 93) “0")}}lpxelinux.0{{else}}boot x64.efi{{end}}

That how make choices for client what they should boot for.




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