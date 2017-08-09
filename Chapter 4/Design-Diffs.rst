



Difficulties in Design
======================

There are quite a few design difficulties to consider when building infrastructure.

Dealing with heterogeneity
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

	There can be many differences across systems, so the infrastructure may work for one operating system but not another. This requires a design that can handle system differences without needing to create a new design for each system. Unfortunately, systems often have different behaviors and might attempt to mix and match different components.

How much does the user know about what they are booting? 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

	This is the issue of previous versus discovered information. In many designs, the user needs prior knowledge of the network they are booting in order to make decisions and bootstrap the program successfully. Often this knowledge is used to pre-populate information manually. While it is an option, this requirement of prior knowledge makes bootstrapping the program much more difficult and time-consuming. Matching information to where it needs to go is a big deal and can be a considerable time constraint. Clearly there is value in a design that allows for the discovery of required information during the process. 

Deciding when and how often to run the boot process
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

	The standard practice has been to tear down infrastructure once it is done. However, a new school of thought has emerged that seeks to keep the infrastructure running, and to allow frequent booting. This concept relates to immutable infrastructure, which is infrastructure that does not change but is able to work in a repeatable fashion. When designing infrastructure, it must be decided when processes should be run and the frequency with which they should run. 

Closely controlling who has access to the system
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

	Someone who has access to a system's data center can do just about anything to the system. This is a very important design consideration as it concerns security. The level of access given within the system should be designed with the level of paranoia of the system administrator(s) in mind. For a more in-depth look, see Chapter 4.3 "Security." 

How to handle out-of-band management (OOBM)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

	All servers have an additional interface: IPMI which provides options for out of band management and monitoring. This opens another important consideration; whether or not OOBM should be made part of the boot provision. OOBM can be used to turn PXE on and off which can prevent broadcast storms and is useful for security reasons. However, this also creates a challenge for OOBM as it can overwhelm the DHCP server. A better path is to always DHCP boot, which still gives the administrator control of the system and has only a small chance of overwhelming the DHCP. 

Figuring out IP address allocation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

	Many operators often want to receive their IP addresses is a specific format, especially when they are receiving a large number of IP addresses, which creates an additional design consideration for the infrastructure. For example, an operator may want the IP addresses to be sent to them organized by interface, with each interfaces' IP addresses to have the same last octet. While this is an understandable request, it is unfortunately complex to implement. 

Issues with rack servers
~~~~~~~~~~~~~~~~~~~~~~~~

	Rack servers, also referred to as rack-mounted servers, are a useful way to consolidate server storage and save floor space. Clients often have second layer boundaries between racks, which means that the racks cannot communicate with each other. The second layer refers to the Open Systems Interconnection (OSI) model in which networks have seven layers. For more details on the OSI model, refer to Chapter 3.1 "Getting on the Network."

Interaction of components 
~~~~~~~~~~~~~~~~~~~~~~~~~
	The switch topology, which refers an organizational representation of the channels and relays in a switch module, might impact DHCP and nextboot provisioning. Depending on how the infrastructure is being built, design may need to take into consideration how changing one component will affect another. 

Deciding on the sourcing of images
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

	Images can be sourced either as Kickstart/Preseed images or as DD images. DD (which means essentially disk copying) is a cloud-based approach and is useful for maintaining images and improving speed. However, DD is very sensitive and can be flaky. So while DD may give a better performance, it will require more individual care. Kickstart, also referred to as Preseed, is the generic image source and is more change-tolerant. Kickstart/Preseed is the main Linux technology and Digital Rebar's default image source.

One last difficulty to note is creating access to PXE boot infrastructure, also referred to as provisioning boot infrastructure. 
