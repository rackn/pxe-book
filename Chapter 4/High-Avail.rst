



High Availability
=================

A number of environments consider high availability, or HA, to be just the ability to make a back-up of data and recover it within a certain time window. For anyone doing high availability work, the first questions they need to ask themselves is: What is their actual performance requirement? Can they have the systems down for several hours at a time? Then it is okay to have high availability by creating and being able to re-create infrastructure quickly.

what are the performance requirements?
	okay w. systems down for a while? then high avail to boot servers

Traditionally, boot provisioning was not considered a high availability service. DHCP is also often not considered high availability because if the leases are still active, there is no need to communicate with the DHCP servers. 

The lease times need to be longer than the high availability windows.

High availability infrastructure is expensive, so it is important to only use it if it is truly needed.

There are some instances, like when establishing new infrastructure, where high availability is needed. relying for updating OS, reboot OOBM, API driven services does point to HA need. 

It is difficult to combine DHCP with high availability infrastructure because DHCP is a protocol for responding to a broadcast message.  HA bc protocol is responding to broadcast. don't want race for answers unless they all give same answers: 2 opt: multiple DHCP servers w/ all same data. or multiple DHCP servers and elect a leader. RAFT protocol to elect leader DHCP using consul/etcd. if you can have DHCP infra manage broadcast, then you can have multiple DHCP servers.

distribute DHCP servers and have second system forward to other systems (Greg design question)

HA provisioning = DHCP servers are aware of multiple nextboot targets. need to have DHCP change nextboot to available server. cant use trad load balancers. bc TFTP doesnt support load balancers.

if multiple provisions then you must synchronize info with data store or site that manages synchronization. problem: boot images can be big so you have to replicate boot images a lot. alt: distribute primary and have every one point to a central back-up so less data synchronization

tl;dr: rebooting more often who have to deal with DHCP provisioning becoming integral part of HA infra. 

Digital Rebar prov can be backed by consul/etcd for HA config. still nedd leader election and data distribution
