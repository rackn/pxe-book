



Network Bandwidth
=================

Provisioning can be very network-intensive because it involves transferring entire operating images from one system to another. It can be even worse if a large number of canned images are being sent. Exceeding the network's bandwidth creates what are called network or broadcast storms, where a large enough portion of the network's resources are consumed by the storm that the network cannot handle normal traffic.

For this reason, it is important to be aware of and monitor provisioning on low links across racks. The network bandwidth issue is compounded by the fact that these networking environments do not know what they have not been explicitly told. The protocols do not have a lot of redundancy built into them for that fact. Users have to be able to deal with networking issues, which is why many people switch from PXE to iPXE.

This is...

The Bandwidth Problem
~~~~~~~~~~~~~~~~~~~~~~

PXE/TFTP is more bandwidth- and networking-sensitive than iPXE/HTTP. As discussed in Chapter 3.6 "Stage Two: iPXE and HTTP," TFTP is error-prone, unsecured, only able to boot from a local area network, and much slower than HTTP.

The way around the issues with PXE/TFTP is a two-stage install. The two-stage install involves a minimal TFTP component, with the majority of the downloading done using an HTTP connection. This method is Digital Rebar's default Discovery. Note that this type of install does require some specialization. 

It is difficult to decentralize DHCP and provisioning infrastructures because everything needs to be synchronized.
There is a tendency to establish only one DHCP server per region, which creates a network congestion point if there is a massive re-provisioning burst and single point of failure when something goes wrong. This tendency is coupled with the desire to reboot all the servers in a data center at the same time, which is quite unrealistic.

This is where the idea of maximum load, or the capacity of the server that is doing the network provisioning, comes in. 

Some people use a torrent system to get around the maximum load issue because torrent distributes bandwidth requirements across multiple servers. However, there are those who do not want to use torrent and using a torrent system still requires that a certain amount of the infrastructure be bootstrapped. In this case, the optimal solution is to either orchestrate a way to stage the bootstrapping environments or create a distributed provisioning infrastructure where you could put provisioners in the top-of-rack switch or on a smaller block on nodes to tighten the scope of the provisioning in order to avoid crossing a large amount of networking segments. This solution requires synchronization across all the information, which is additional management layers on provisioning. 

Fortunately, DHCP servers do not use much bandwidth; the real bandwidth hog is TFTP boot. 

The two-stage installer mitigates bandwidth hogging by keeping the boot images small and light, and to create a random back-off to distribute the provisioning load. There is, however, the risk of some servers no longer trying to PXE boot after a certain number of attempts so they time-out and never end up coming online. 

