



Difficulties in Design
======================

A list of difficulties in design:

-Creating access to PXE boot infrastructure, also referred to as provisioning boot infrastructure. 

-Dealing with heterogeneity. There can be many differences across systems, so the infrastructure may work for one operating system but not another. This requires a design that can handle system differences without needing to create a new design for each system. Systems might have different behaviors and might want to mix and match different components.

-How much does the user know about what they are booting? This is the issue of previous knowledge versus discovered information. In many designs, the user needs prior knowledge of what they are booting in order to make decisions and bootstrap the program, often in the form of having to pre-populate information themselves. But this requirement of prior knowledge makes bootstrapping the program much more difficult. Matching information to where it needs to go is a really big deal. The design difficulty is in setting up the program so that the user can discover the information they need as they go through the process. 

-Figuring out when and how often to run the boot process. The standard has been to tear down infrastructure once it is done. However, a new school of thought is to keep the infrastructure running, and to have boot frequently. Relates to immutable infrastructure. In design, there needs to be a decision made of when processes should be run and the frequency with which they should run. 

-Need to closely control who has access to the system. Someone who has access to a system's data center can do just about anything to the system. This is a very important design consideration as it concerns security. The level of access given within the system should be designed with the level of paranoia of the system administrator(s) in mind. For a more in-depth look, see Chapter 4.3 "Security." 

-How to handle out-of-band management (OOBM). All servers have an additional interface: IPMI. Need to decide if OOBM should be made part of the boot provision. OOBM can be used to turn PXE on and off which can prevent broadcast storms and is useful for security reasons. However, this is what creates the OOBM challenge. A better path is to always DHCP boot, which still gives the administrator control of the system and has only a small chance of overwhelming the DHCP. 

-Figuring out IP address allocation. Many operators often want to receive their IP address is a specific format, especially when they are receiving a large number of IP addresses which creates an additional design consideration when building up the infrastructure. For example, an operator may want the IP addresses to be sent to them organized by interface, with each interfaces' IP addresses to have the same last octet. While this is an understandable request, it is unfortunately quite difficult to implement. 

-Issues with rack servers (also called rack-mounted servers). Rack servers are a useful way to consolidate server storage and save floor space. Clients often have second layer boundaries between racks, which means that the racks cannot communicate with each other. The second layer refers to the Open Systems Interconnection (OSI) model in which networks have seven layers. For more details on the OSI model, refer to Chapter 3.1 "Getting on the Network."

-Interaction of components. The switch topology (switch topology is an organizational representation of the channels and relays in a switch module) might impact DHCP and nextboot provisioning. Depending on how the infrastructure is being built, design may need to take into consideration how changing one component will affect another. 

-Deciding on the sourcing of images. Images can be sourced either as Kickstart/PreSeed images or as DD images. DD (which essentially means disk copying) is a cloud-based approach and is useful for maintaining images and improving speed. However, DD is very sensitive and can be flaky. So while DD may give a better performance, it will require more individual care. Kickstart, also referred to as PreSeed (two main linux technologies), is the generic image source and is more change-tolerant. Kickstart is Digital Rebar's default image source.