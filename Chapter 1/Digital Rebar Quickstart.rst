



Digital Rebar Provision Quick Start
=============

This quick start guide provides a basic installation and starting point for further exploration.  The guide has been designed for UNIX systems: Mac OS, Linux OS, Linux VMs and Linux Packet Servers.  The guide employs Curl and Bash commands which are not typically considered safe, but they do provide a simple and quick process for start up.  These commands will allow for an easy set-up procedure, but please be aware that this is not a full install and that this quick start guide is intended to act as an educational aid, not as a true installation guide.  For a complete installation guide see chapter 5, or for more up to date information on Digital Rebar Provision, contact the Digital Rebar Team at <RACKN TEAM CONTACT INFO>.

To begin, execute the following command in a shell or terminal: 

  ::

    curl -fsSL https://raw.githubusercontent.com/digitalrebar/provision/master/tools/install.sh | bash -s -- --isolated install

The command will pull the latest code bundle and checksum from GitHub, extract the code files, verify prerequisites are installed, and create some initial directories and links.

The terminal should then display something like this:

  ::

    # Run the following commands to start up dr-provision in a local isolated way.
    # The server will store information and serve files from the drp-data directory.

    sudo ./dr-provision --static-ip=<IP of an Interface> --file-root=`pwd`/drp-data/tftpboot --data-root=drp-data/digitalrebar &

    # Once dr-provision is started, this command will gather and upload the tools required to
    # do discovery-based machine management

    tools/discovery-load.sh

The next step is to execute the sudo command which will run an instance of Digital Rebar Provision that uses the drp-data directory for object and file storage.  Additionally, *dr-provision* will attempt to use the IP address best suited for client interaction. However, if that detection fails, the IP address specified by *--static-ip* will be used. After DRP has started, a prompt for a username and password will appear.  

The default username and password is ``rocketskates & r0cketsk8ts.``

With DRP running it is now time to install the specialized DRP images and the required boot environments.

The *tools/discovery-load.sh* command will use the default credentials to install the discovery, sledgehammer, and local boot environments.  This will download the sledgehammer tarball and upload into Digital Rebar Provision. It will also change the default and unknown boot environments to do dynamic discovery.  This script needs to be run after beginning *dr-provision*.

When the *tools/discovery-load.sh* script finishes Digital Rebar Provision will be installed and operational.  


.. note:: This quick start guide does NOT create a production deployment and the deployment will NOT restart on failure or reboot.

.. note:: Remember to check Chapter 5 for general install information.
.. note:: Remember to check :ref:`rs_arch_ports` in the Digital Rebar Provision documentation if there are port access issues.