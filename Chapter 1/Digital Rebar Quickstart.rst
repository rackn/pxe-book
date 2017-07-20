


Digital Rebar Quick Start
=========================  

Curl/Bash is NOT safe, but it is fun and easy.

Load the following into the terminal:
 
  	||| curl -fsSL https://raw.githubusercontent.com/digitalrebar/provision/master/tools/ 
  	|||  install.sh | bash -s -- --isolated install  									    

This will pull the latest code bundle and checksum from github, extract the code files, make sure prerequisites are installed, and create some initial directories and links. It should display something like this:


	||| # Run the following commands to start up dr-provision in a local isolated way.
	||| # The server will store information and serve files from the drp-data directory.
	|||
	||| sudo ./dr-provision --static-ip=<IP of an Interface> --file-root=`pwd`/drp-data/tftpboot --data-root=drp-data/digitalrebar &
	|||
	||| # Once dr-provision is started, this commmand will gather and upload the tools required to
	||| # do discovery-based machine management
	|||
	|||tools/discovery-load.sh

The sudo command will run an instance of Digital Rebar Provision that uses the drp-data directory for object storage and file storage. Additionally, dr-provision will attempt to use the best IP address for client’s to talk to it, but if that detection fails, the IP address specified in by –static-ip will be used.

The default username: password is rocketskates:r0cketsk8ts.

The tools/discovery-load.sh command will use the default credentials to install the discovery, sledgehammer, and local boot environments. This will download the sledgehammer tarball <need definition for "sledgehammer tarball"> and upload it into Digital Rebar Provision. Additionally, the tools/discovery-load.sh command will change the default and unknown boot environments to do dynamic discovery. This script needs to be run after starting dr-provision.

Note: 
	This is not a production deployment and will not restart on failure or reboot.
	Remember to check Install <page ref> for general install information.
	Remember to check Ports <page ref> if you are having port access issues.


