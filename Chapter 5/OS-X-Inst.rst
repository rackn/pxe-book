



Installing On OS X
==================

	In this section, we will walk through how to install Digital Rebar Provision on a Mac. 
You will need the bsdtar and p7zip packages before installation. Tar must be at least version 3.0.0. 

	Open your computer's terminal and enter the following command: curl -fsSL https://
raw.githubusercontent.com/digitalrebar/provision/master/tools/install.sh | bash -s -- --isolated install

	This will pull the latest code bundle and checksum from github, extract the code files, 
make sure prerequistes are installed, and create some initial directories and links. If you do not have the necessary version of tar, it will display this:

<insert screenshot>

	If this occurs, you will need to install Homebrew from https://brew.sh.

	Once you have the pre-requisites, download a version of Digital Rebar Provision from 
www.github.com/digitalrebar/provision/releases and use the Curl command again: curl -fsSL https://raw.githubusercontent.com/digitalrebar/provision/master/tools/install.sh | bash -s -- --isolated install. 

	Make sure the permission of /bin/[os]/[architecture]/dr-provision is executable using 
'chmod +x ./bin/linux/amd64/dr-provision' and run it using 'sudo ./bin/linux/amd64/dr-provision'


Go to https://localhost:8092 

<insert screenshot>

and enter the default username and password which is rocketskate:r0cketsk8ts.

<insert screenshot>






  