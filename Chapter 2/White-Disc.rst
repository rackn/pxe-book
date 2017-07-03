



White-list or Discovery
======================= 

Like most accessible servers, a PXE-booting server can be run with a white-list. However, white-lists require processing and storing the mac (physical) addresses of every machine within the network. If data management and transfer are simple and accurate then by all means use them. However, if data management and transfer seem like a waste of resources then there is a better option: discovery. 

There are two types of discovery, active and passive. In active discovery, much as in active sonar or radar, the control machine sends out a "ping" of some sort and the other machines on the network respond to that ping.

<Active Discovery Graphic>

Passive discovery is again similar to passive sonar and radar in that the control machine just listens for machines on the network. The control machine then gathers the information from these requests. 

<General Passive Discovery Graphic>

In Digital Rebar Provisioner, the control machine has two channels over which it can listen: DHCP and HTTP/TFTP (file serving). When DHCP hands out addresses DRP records information that tracks the IP address to the MAC address for each machine, and additionally it records information regarding the lease.

<DRP Passive Discovery Graphic>

Then when the DHCP system directs machines to boot the DRP image the machine will register with DRP and then eventually inventory the nodes running on the machine. At this point a machine is fully inventoried and discovered. Other discovery methods will work differently, but DRP is a fairly simple example.
