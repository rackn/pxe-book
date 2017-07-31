




High Availability
=================

A number of environments consider HA, or HA, to be just the ability to make a back-up of data and recover it within a certain time window.  For anyone doing HA work, the first question they need to ask themselves is: What is their actual performance requirement?  If they can have the systems down for several hours at a time, then it is okay to have HA which allows for the ability to re-create infrastructure quickly.  

Traditionally, boot provisioning is not considered a HA service. DHCP is also often not considered a HA service because if the IP address leases are still active, there is no need to communicate with the DHCP server.  Ultimately, the lease times need to be longer than the HA windows by a significant amount. 

Because HA infrastructure is expensive, it only makes sense to acquire it when it is truly needed, such as in the cases below. 

There are some instances, especially with establishing new infrastructure, where HA is needed. Reliance on the DHCP servers and the provisioning infrastructure for updating operating systems, re-imaging infrastructure, managing booting, handling OOBM, and other API-driven services does point to a need for HA infrastructure. 
  
Digital Rebar Provisioning can be backed up by data storage centers such as consul or etcd to distribute its HA configurations. That is not enough in itself, and so there is still a need to deal with leader election and data distribution.  

Dealing with Distributed DHCP Environments
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This is where system forwarding comes in. If all of a user's networks need the services of DHCP servers, the choice is between giving each network its own DHCP server (a managerial nightmare) or having the router environment forward DHCP requests from all the networks to a single DHCP server or one set of DHCP servers. The second choice is the distributed DHCP method. This is done with a boot or DHCP forwarder. Most high-end servers can forward. In HA mode, the user needs to forward to multiple DHCP servers and multiple IP addresses.

HA DHCP
~~~~~~~
 
All of the networks need to have a DHCP server or set of servers that can handle all of the requests. This way, if one of the servers dies there is still a path for the networks to send out data. DHCP does not understand HA because DHCP assumes there is only one entity in charge of device addresses. The work-around for this is to force-assign addresses to devices and have MAC-IP binding for each node. 

Because DHCP is a protocol for responding to a broadcast message, HA DHCP raises the issue the DHCP servers racing to answer requests, unless the servers are guaranteed to give the exact same answer.  In that case, there are a few options. All the DHCP servers can be set up to use the same data, or out of the set of DHCP servers one can be elected as the leader that will answer requests.  The way to do this is with the consensus protocol, Raft.  Raft elects a leader using consul or etcd.  If DHCP servers can manage broadcast, then multiple DHCP servers can be set up. 

Another option is active and passive DHCP servers. The active DHCP server provides data and answers requests while the passive server monitors it. If the active server goes down, the passive server is able to pick up its responsibilities. DRP avoids downtime during this switch by saving the DHCP information in shared storage areas (like consul) so that the passive server can load the information as soon as the active server goes down. 


HA Requirements Beyond DHCP
~~~~~~~~~~~~~~~~~~~~~~~~~~~

HA requires that a file server always be available. The traditional solution to this problem is to have load balancers in front of access points for HTTP endpoints so they are always available. DRP handles this  by dynamically building references to API servers so the IP address is always injected when needed. Both methods work well and can be used in tandem. 


HA provisioning means that the DHCP servers are aware of multiple nextboot targets.  The DHCP servers need to be able to change the nextboot to an available server. This cannot use traditional load-balancers because TFTP does not support load balancing.  

If there are multiple provisioners, then all the information must be synced for them using a shared data store or by using a site that manages synchronization.  The issue with this is boot images can be large, and having multiple provisioners might require replicating boot images where they are not needed. The alternative is to distribute the primary and have every machine point to a central back-up. 

In short: In an environment with the expectation of rebooting and provisioning more often, DHCP and provisioning will become an essential part of the HA infrastructure.  

