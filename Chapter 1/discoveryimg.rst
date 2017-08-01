


Discovery Image: Install Discovery Bootenv
==========================================

As discussed in chapter 2.4, the two classes of network registration: white-list and discovery. White-list, as the name implies, is registration from a predetermined list of machines and requires a lot of information to operate correctly. With white-list, the Discovery Image is not required, and all of the machines in the network could be created inside DRP machine entries by assigning names and IP addresses into the system. This process is doable, but very time-intensive and error prone. Fortunately, Digital Rebar Provisioner comes equipped with Sledgehammer, DRP's discovery image.  

Sledgehammer is a RAM-only Centos Image that provides inventory information about the network. It is stored in an S3 Bucket with Amazon Web Services (AWS) which allows discovery to pull a reference sledgehammer image. Discovery then sets up DRP to serve the image. When a request comes in for the DHCP serer, it can provide that machine with a Sledgehammer kernel to log the machine's information.  

For security reasons DHCP servers have the 'default unknown machine boot environment' variable set to 'No,' as this protects the network from security breaches. With this variable setting, the DHCP server will not register new machines which send it requests, protecting it from potential security hazards. If Sledgehammer is allowed to register every machine without supervision, it can include and register unintended machines which poses a significant security risk.  

The Sledgehammer Kernel allows the system to inventory itself and then to register itself with DRP. These registered machines then appear in the DRP UI and can then be edited or accessed remotely.  



