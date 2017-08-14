


Getting Started
===============

This section guides users through the steps needed to begin Digital Rebar Provision also referred to as DRP.  Digital Rebar Provision is a stand-alone version of the PXE/DHCP/TFTP system used by the broader Digital Rebar project.  It is a great first step for the larger deployments and sufficient for those just looking to replace Cobbler or another metal provisioner (MaaS, Stacki, Foreman, USB, etcetera).  DRP does not have out-of-band or firmware features - those services remain under the project umbrella, but are not included in the provisioner.

For Mac and Linux, the first step is to download DRP and make sure that the DHCP is isolated. From there, go to Chapter 5.1 "Installing on OS X," or Chapter 5.2 "Installing on Linux with Kickstart and Preseed."

Unfortunately, Digital Rebar Provision and Windows do not get along very well. For this reason, it is highly preferable to run a virtual machine with a Linux OS on a Windows physical machine.  This means using a VM monitor, of which Virtual Box is most compatible with DPR.  Additionally, the DRP install will require a DHCP and a PXE server for any real testing or usage.  After establishing the VM, refer to Chapter 5.2 "Installing on Linux with Kickstart and Preseed" for detailed instructions for a Linux install. 

In all virtual machines, be they on-site or through a service like Packet or Amazon Web Services, the first step is to host the virtual machine with Linux. The next step is installing DRP. The instructions for Packet VMs are continued in Chapter 5.3 "Installing with Packet." 
