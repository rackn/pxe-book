




High Availability
=================

A number of environments consider high availability, or HA, to be just the ability to make a back-up of data and recover it within a certain time window. For anyone doing high availability work, the first question they need to ask themselves is: What is their actual performance requirement? If they can have the systems down for several hours at a time, then it is okay to have high availability which allows for the ability to re-create infrastructure quickly.

Traditionally, boot provisioning is not considered a high availability service. DHCP is also often not considered a high availability service because if the IP address leases are still active, there is no need to communicate with the DHCP server. Ultimately, the lease times need to be longer than the high availability windows by a significant amount. 

Because high availability infrastructure is expensive, it only makes sense to acquire it when it is truly needed, such as in the cases below. 

There are some instances, especially with establishing new infrastructure, where high availability is needed. Reliance on the DHCP servers and the provisioning infrastructure for updating operating systems, re-imaging infrastructure, managing booting, handling OOBM, and other API-driven services does point to a need for high availability infrastructure. 

It is difficult to make DHCP highly available because DHCP is a protocol for responding to a broadcast message. The goal is to avoid a race between the DHCP servers giving answers to a request unless the servers are guaranteed to give the exact same answer. In that case, there are two options. Either set up all the DHCP servers using the same data, or out of the set of DHCP servers elect one as the leader that will give the answers to requests. The way to do this is with the consensus protocol, Raft. Raft elects a leader using consul or etcd. If DHCP servers can manage broadcast, then multiple DHCP servers can be set up. 
Digital Rebar provision can be backed up by consul or etcd data storage to distribute its high availability configurations. That is not enough in itself, and so there is still a need to deal with leader election and data distribution. 

***distribute DHCP servers and have second system forward to other systems (Greg design question)

High availability provisioning means that the DHCP servers are aware of multiple nextboot targets. The DHCP servers need to be able to change the nextboot to an available server. This cannot use traditional load-balancers because TFTP does not support load balancing. 

If there are multiple provisioners, then all the information must be synced for them using a shared data sotre or by using a site that manages synchronization. The issue with this is boot images can be large, and having multiple provisioners might require replicating boot images where they are not needed. The alternative is to distribute the primary and have every machine point to a central back-up. 

In short: In an environment with the expectation of rebooting and provisioning more often, DHCP and provisioning will become an essential part of the high availability infrastructure. 


