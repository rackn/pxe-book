



Installing On OS X
==================

<<<<<<< HEAD
This section covers how to install Digital Rebar Provision on a Mac. 
The bsdtar and p7zip packages are needed before installation. Additionally, Bsdtar must be at least version 3.0.0. 

Open the computer's terminal and enter the following command: curl -fsSL https://
raw.githubusercontent.com/digitalrebar/provision/master/tools/install.sh | bash -s -- --isolated install

This will pull the latest code bundle and checksum from github, then extract the code files, next
make sure prerequisites are installed, and finally create some initial directories and links. If the user has not installed the necessary version of tar, the computer will display this:

<insert screenshot>

If this occurs, Homebrew will need to be downloaded and installed from https://brew.sh.

After the pre-requisites have been installed, download a version of Digital Rebar Provision from www.github.com/digitalrebar/provision/releases and use the Curl command again: curl -fsSL https://raw.githubusercontent.com/digitalrebar/provision/master/tools/install.sh | bash -s -- --isolated install. 

Confirm that the permission of /bin/[os]/[architecture]/dr-provision is executable by using 
'chmod +x ./bin/linux/amd64/dr-provision' and then run it using 'sudo ./bin/linux/amd64/dr-provision'

Go to https://localhost:8092 

<insert screenshot>

and enter the default username and password, which is rocketskate:r0cketsk8ts.

<insert screenshot>
