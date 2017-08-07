



Getting on the Network
======================

This section covers how to add a new machine to the network. To join a network, a machine must receive an IP address from the DHCP server.  Before continuing, there are some definitions and basic terms that need to be covered.  

Dynamic Host Configuration Protocol (DHCP) is a client-server protocol that enables a server to automatically assign IP addresses to a subnet.  DHCP is needed to provide a new machine with an IP address for the network it is on.  One way to look at how to DHCP server and the machine communicate is with the Open Systems Interconnection (OSI) model.  In the OSI model, the network has seven layers which are, from bottom to top: physical, data-link (or protocol), network, transport, session (also called port), presentation, and application.  

<insert OSI model graphic>

A computer's MAC, or physical, address is located in the second layer and is guaranteed by the manufacturer to be unique.  There is also a local IP address, located in the third layer, that is given by the DHCP server and is unique for the network.  The network refers to the group of devices that share a connection to a server.

The goal of getting on the network is for the new machine to be able to communicate with other devices on the network by receiving an IP address from the DHCP server. 

Of course it is not that simple and there is a problem: all new machines have no knowledge.  Meaning, they have no idea how to access the network and communicate with the other devices.  New machines first need to learn about the structure of the network to know what ports to employ for communication.  

A machine's IP address, in the third layer, has two protocols that are located in the fourth layer: User Datagram Protocol (UDP) and Transmission Control Protocol (TCP).  UDP is simpler while TCP is more complex.  Both protocols have a port that they broadcast and receive information from.  The port layer is similar to a switchboard, because the DHCP server must be listening on the port from which the machine is broadcasting in order to communicate.  New machines do not have an IP address stored in the third layer, but can use the protocols from the 4th layer to ask for an IP address from the DHCP server.  

The machine broadcasts a UDP packet in the fourth layer on port 67, which goes out to all the devices on the network.  The DHCP server receives the UDP packet and sends its own UDP packet back to the new machine on port 68.  This UDP packet includes the unique IP address, as well as other information that will be covered in the next section (3.2).  Now that it has an IP address, the machine can get on the network. 

In very basic terms, the exchange looks like this: 

<insert graphic
DHCP Server <-----(I'm here)---- Machine
DHCP Server -----(IP address)--> Machine >
