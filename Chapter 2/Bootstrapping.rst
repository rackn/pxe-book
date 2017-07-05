



What is Bootstrapping?
======================

"Bootstrapping" as a term for computing emerged in the 1950's. Once an initial program is started, the computer boots itself through a series of simpler programs that serve to start up more complex programs. This goes on until the computer is fully booted, having, following the adage, "pulled itself up by its bootstraps." The operating system is stored on firmware, often a disk or ROM. The initial kernel, also referred to as the "bootstrap loader," searches for, initializes, and tests other programs needed to start up the operating system. 


There is also bootstrapping specific to nodes. These bootstrapping nodes, also known as rendezvous hosts, give configuration information to nodes new to the network to help them join. A rendezvous host makes it so the user does not need people to initialize each new node. A new node needs configuration information or else it will not be able to join the network and communicate with other nodes. 

Within Digital Rebar, Sledgehammer is a bootstrapping tool used to perform initial node discovery and register its discovered state within the Digital Rebar node provisioning framework. 