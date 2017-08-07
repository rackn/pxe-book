



Stage Two - iPXE & HTTP
=======================

Chapter 3.1, "Getting on the Network," covered networking booting with DHCP.  This section concerns the second stage of the two-stage TFTP/HTTP boot.  

Digital Rebar's specialized Sledgehammer and Discovery images are designed for rapid installs with optimized install cycles that improve boot speed by switching from PXE TFTP to iPXE HTTP in a two-stage process.  This ensures maximum hardware compatibility without creating excess network load.  

When the new machine requests an IP address from the DHCP server, the machine processes the UDP packet from the server using TFTP with standard PXE.  However, TFTP has several issues.  It is error-prone, unsecured because there is neither access control of content nor login ability, and can only boot from a local area network.  TFTP is also much slower than HTTP, making HTTP a preferable alternative.  

After the machine has received the UDP packet from the DHCP server, the machine then retrieves, loads, and executes iPXE (via TFTP), which in turn sends out a DHCP request.  iPXE is given the name of a file on the HTTP server which switches the processing from TFTP over to HTTP.  This switch increases the speed because HTTP is much faster than TFTP.  

< iPXE is the open-source version of PXE and is available at http://ipxe.org. ???> 

When networking booting, HTTP can also be used to load additional content.  Furthermore, HTTP supports encrypted transmissions for situations where network security is threatened. 




