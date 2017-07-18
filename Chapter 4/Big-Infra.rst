



Big Infrastructure
==================

This section covers special concerns for those who have thousands of nodes. 

With thousands of nodes, performance becomes a huge issue. Having several rack servers of nodes boot at the same time and the time it takes to run a provisioning infrastructure is high.

Big infrastructures have a tendency to cycle more often, and they need to be API-driven. When working in the scope of one thousand plus node infrastructure, there is an expectation that those servers are not being maintained in real-time by human employees. There also may be failed servers that are left in place because servers are not being fixed immediately. In one possible scenario, a company may only send out technicians to fix servers one day a week. This means that any provisioning infrastructure must be able to be turned off or stopped from notifying if it cannot provision something. 

People who have big infrastructures tend to not use vendor OOBM tools because of the cost and the scale, so they have fewer options in terms of infrastructure management. Additionally, they have a tendency to use less expensive servers due to their scale, and those servers which may have flakier BIOS configuration. 

<insert stories of bad experiences with inexpensive servers>
Example of lower-cost server: when it couldn't PXE boot after three tries it gave up. Person had a 400-node infrastructure with a white box that after trying to PXE boot three times and then failing it would shut off. When their PXE infrastructure was overloaded and started having issues with the TFTP traffic, a significant number of servers would not recover after a reboot. This meant employees had to be sent out to the data center to hard power cycle the servers that had not recovered or they had to search to identify the servers that had no recovered.


Most big infrastructures are remotely operated. Identifying each node is difficult and time-consuming. There is a tendency to turn the machines on and off quite a bit more due to rotating the machines or during a bring-up cycle where they are re-provisioning a large number of the machines. In some cases they have a tendency to use less complex networking topology, but there are also those who are more likely to use layer 2 segmentation per rack due to worrying about network storms. 

Another challenge in big infrastructure is having multiple teams that need to collaborate but have different access. For example, the networking team and the server team might have to coordinate activities to handle boot provisioning. 

Big infrastructure managers are often very concerned with time. They are willing to spend more time optimizing their systems and more likely to use a disk imaging approach. Typically much more consistent inside of infrastructure and the nodes so the system is much more homogeneous. 

<should the collective noun be 'big infrastructure people' 'big infrastructure clients' just 'big infrastructure?' I've used a mix of them in this first draft of the section>



