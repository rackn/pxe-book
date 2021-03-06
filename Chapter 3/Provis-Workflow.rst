



Provisioning Workflow
=====================

Generally, provisioning workflows can be broken down into two steps: Discovery and OS Install.  These steps begin with network discovery (see chapter 3.1) providing a “nextboot” instruction to the server’s pre-execution environment (PXE).  That environment can download a very limited operating system using an equally simple file transfer protocol: TFTP.  That next operating system can then take more complex actions, including using HTTP to download further files.  This chapter will go into detail about the different stages of provisioning.  

With Digital Rebar, the basic discovery flow uses the specialized Discovery and Sledgehammer boot environments.  These boot environments work with the default nextboot to self-register machines with Digital Rebar Provision using the machine's API.

The discovery flow is highly valuable when deploying to large networks, as it reduces the amount of required information and removes the need to manage data on individual machines.  Without the discovery flow, operators would have to maintain information on every machine in the network.  

<Add Discovery Image>

Once systems have been discovered using Basic Discovery, their machine boot environments can be set to an OS installation image.  The recommended boot environments for these images includes an automatic machines API call that sets the machine to boot to local disk.  

<Add Unknown Network Image>

Finally, there is the option to skip the discovery flow and instead move directly into OS installation.  Provisioning on a known network requires complete knowledge of the network and the machines of which it is comprised.  This method is faster because it skips discovery in favor of determining machine definitions in advance using spread sheets, stone tablets, Ouija boards or other 1990s data center inventory management techniques.  However, speed comes at a price. This method requires lots of data entry and is therefore susceptible to human error.  Regardless of which technique is used, provisioning a known network is very labor-intensive, especially if the pre-requisite data is not on hand. 

<Add Known Network Image>