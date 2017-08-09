




Working OS: Install Centos Bootenv
==================================

It is important to not get so caught up in the act of provisioning and take a moment to ask what it is that the provisioner is attempting to install.  Digital Rebar Provisioner has two bootenvs standard which allows it to boot either Centos 7.3 or Ubuntu <Insert Version Here> as of August 2017.  The provisioner has a boot environments for both and the prerequisite templates that both OS's need to properly boot.  

Once a machine has been discovered or created, the machine's boot OS needs to be changed to the install OS, typically one of the two DRP standard OS's.  Then, after switching the OS, the machine must be rebooted, and the new OS will be installed.  Unfortunately PXE must go through its boot process every time the machine attempts, but fails, to boot.  After a successful install, machines can be ordered to boot from the local disk which will the only reboot the install OS. 

For Centos the boot environment will begin by installing the OS with root user and password set to 'rocketskates.'  

The Ubuntu Image specifically provides a pre-seed file and then a post-install file for the boot environment.  The Ubuntu OS also has the default user and password set to 'rocketskates' with sudo privileges to root. 

Furthermore, DRP provides increased utility by enabling the injection of SSH keys for post-install access, this is done with the root install SSH template.  The purpose of SSH is to allow users to access the server without a password for each individual login.  This allows for individual machine management from a root level and is a useful tool for the system administrator. 
