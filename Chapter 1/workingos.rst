



Working OS: Install Centos Bootenv
==================================

It is important to not get caught up in the act of provisioning and take a moment to ask what it is that the provisioner is attempting to install.  Digital Rebar Provisioner has two bootenvs standard which allows it to boot either Centos 7.3 or Ubuntu <Insert Version Here> as of August 2017. DRP has boot environments for both and the prerequisite templates that both OS's need to properly boot.  

Once a machine has been discovered or created the machine's boot OS needs to be changed to the install OS, typically one of the two DRP standard OS's.  Then, after switching the OS, the machine must be rebooted, and the new OS will be installed.  Unfortunately, PXE must go through its boot process every time that the machine attempts, but fails, to boot. After a successful install, machines can be ordered to boot from the local disk which will only reboot the install OS. When the machines are set to always PXE-boot, the post-install processing sets the bootenv to local, which tells the machine to boot from the local disk. This is a security mechanism, similar to setting "default unknown machine boot environment" to "no" in chapter 1.4. It can be changed if desired. 

For Centos, the boot environment will begin by installing the OS with root user and password set to 'rocketskates.'  

The Ubuntu Image specifically provides a pre-seed file and then a post-install file for the boot environment.  The Ubuntu OS also has default user and password set to 'rocketskates' with sudo privileges to root. 

Furthermore, DRP provides increased utility by enabling the injection of SSH keys for post-install access. This is done with the root install SSH template.  The purpose of SSH is to allow users to access the server without a password for each individual login, which allows for individual machine management from a root level and is a useful tool for the system administrator. 
