



Big Infrastructure
==================

This section covers special concerns and challenges when dealing with systems containing a large number of nodes.  

With thousands of nodes, boot performance becomes a huge issue.  Having several rack servers of nodes boot at the same time is very time-intensive, and it takes a significant amount of time to run a provisioning infrastructure.  

Additionally, big infrastructure networks have a tendency to cycle more often, and they need to be API-driven.

When working in the scope of a one thousand-plus node infrastructure, there is an expectation that those servers are not being maintained in real-time by human employees.  There also may be failed servers that are left in place because the servers are not being fixed immediately. In one possible scenario, a company may only send out technicians to fix servers one day a week.  This means that any provisioning infrastructure must be toggle-able or stopped from notifying if it cannot provision something.  This creates unique challenges for provisioning these large systems with inherent complex problems.

People who have big infrastructure networks tend to not use vendor OOBM tools because of the cost and the scale, so they have fewer options in terms of infrastructure management.  Additionally, they have a tendency to use less expensive servers due to their scale, and those servers may have flakier BIOS configurations.  These tendencies even further complicate the issues with developing a provisioning solution.  


As mentioned above, lower-cost servers often create more difficulties while provisioning. For example, there is a low cost server that, when it cannot PXE boot after three tries, it gives up.  In this case a client had a 400-node infrastructure comprised of these low cost servers.  Now as long as the servers booted correctly within three attempts the infrastructure setup would have been fine, but of course that was not the outcome.  Any time the client would attempt a large-scale reboot, their PXE infrastructure would overload.  This meant they started having issues with the TFTP traffic, and a significant number of servers would not recover after a reboot, having attempted PXE booting three times, failed, and then shut down.  This meant employees had to be sent out to the data center to hard power cycle the servers that had not recovered. Unfortunately with a 400 node infrastructure, finding individual nodes is a difficult process as they had to search to identify specific servers.  In this situation the operator should have considered investing more in better nodes; if they had done that in the first place, then they might have avoided the cost and annoyance of having to manually cycle the non-functional nodes.  There is not much Digital Rebar Provision can do about this sort of issue, as the fundamental problem lies with the firmware of the cheap nodes and their inability to attempt a reboot. 

Furthermore, most big infrastructures are remotely operated.  Identifying each node is often difficult and very time-consuming.  There is a tendency to turn the machines on and off quite a bit more than in smaller networks due to machine rotations or during a bring-up cycle where the management is re-provisioning a large number of machines.  In some cases, big networks have a tendency to use less complex networking topology, but there are also those who are more likely to use layer two segmentation per rack due to worrying about network storms.  

Another challenge in big infrastructure is having multiple teams that need to collaborate but have different access.  For example, the networking team and the server team might have to coordinate activities to handle boot provisioning.  Fortunately this problem is not so much a technical issue as it is one of coordination.  

Users of big infrastructure are typically very concerned with time and reliability.  Therefore they are willing to spend more time optimizing their systems and more likely to use a disk imaging approach. Their systems are usually much more consistent inside of the infrastructure and the nodes so the system is much more homogeneous.  


