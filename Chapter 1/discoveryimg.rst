


Discovery Image: Install Discovery Bootenv
==========================================


As chapter 2 section 4 discusses in depth there are two classes of network registration.  These two methods are white-list and discovery.  White-list, as the name implies is registration from a predetermined list of machines and requires a lot of information to operate correctly.  With white-list, the Discovery Image is not required, and all of the machines in the network could be created inside DRP machine entries by assigning name and IP address into the system.  This process is completely doable, but very time intensive and error prone.  Fortunately Digital Rebar Provisioner comes equipped with Sledgehammer the DRP discovery image.  

Sledgehammer is a RAM only Centos Image that provides inventory information about the network.  It is stored in an S3 Bucket with AWS which allows discovery to pull a reference sledgehammer image.  Discovery then sets up DRP to serve the image.  Then when a request comes in for the DHCP serer, it can provide that machine with a sledgehammer kernel to log the machine's information.  

For security reasons DHCP servers have the 'default unknown machine boot environment' variable set to "No," as this protects the network from security breaches.  With this variable set to "No" the DHCP server will not register new machines which send it requests, protecting it from potential security hazards.  Generally it is unwise to simply allow sledgehammer to register every machine without supervision as it can include and register unintended machines which might pose a significant security risk.  

The Sledgehammer Kernel allows the system to inventory itself and then to register itself with DRP.  These registered machines then appear in the DRP UI and can then be edited or accessed remotely.  












Multiple ways: 

2 classes

1 prescriptively register every address, know about machines

-DRP Discovery Image: Sledgehammer
--RAM only centos image, provides inventory info and others

---Stored in S3 bucket
---Discovery pulls a reference sledgehammer image and sets up drp to serve the image

When a request comes in the DHCP server can give the machine a kernel
-Typically DHCP default unknown machine boot environment set to no
-system inventories itself and then uses the inventory to register itself with DRP which then appears in UI 

Discovery Image not required, could create inside DRP machine entries by assigning name and IP address into the system
