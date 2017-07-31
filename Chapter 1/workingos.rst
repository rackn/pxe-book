



Working OS: Install Centos Bootenv
==================================

























Import a boot env that represents an install Centos 703 and Ubuntu XXXX
Has a boot env and the required templates with the required config templates and kickstart for Centos
Can have Env inject ssh keys for post install access (Root install ssh template)
Wherever the DRP CLI commands are run if it has internet will auto-import and set up he Centos ISO

The Ubuntu Image provides the boot env and templates: A preseed file and a post install file
also uses root access template to ensure ssh keys are installed/activated

For Centos the boot env by default will install the operating system with the root user and root password as Rocketskates

for Ubuntues the default user is Rocketskates with Sudu privalages to root

once a machine has beed discovered or created the machines boot os needs to be changed to the install os and then rebooted

must PXE boot every time it reboot until the OS installs correctly

Must force PXE boot during doscovery or OS installation if that is not wanted

the Post install boot env to the special "Local" boot env which tells the machine to boot from local disk
the parameter can be set to not local if desired.