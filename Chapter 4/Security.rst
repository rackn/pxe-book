



Security
========

Keeping infrastructure secure needs to be taken very seriously. For any security configuration, there are risks that someone can access the systems and re-image or reboot and destroy data, give themselves access to servers by adding their own keys or user accounts, add back doors into the system, or install malware. Once someone has access to the provisioning infrastructure, it is a very serious security breach.

HTTP and TFTP are not secured protocols and there is no way to secure them. If someone is in the network, it would be possible for them to watch the traffic in the network and see the data that is in it. For that reason, Digital Rebar switches all of their API work on HTTPS (Hyper Text Transfer Protocol Secure) whenever possible. Ultimately, if there is someone on the network watching the traffic, that is a bigger problem that needs to be dealt with. 

The way around dealing with HTTP, TFTP, and HTTPS is to use the vendor's specific OOBM tools to install the operating systems which bypasses PXE/DHCP/provisioning and goes straight into a secured infrastructure. But it is complex and expensive, and locks you into vendor. To improve server security, Digital Rebar recommends rebooting servers frequently, making sure the firmware is patched, limiting access to the infrastructure, minimizing the amount of image deployed in this way, and using fewer patterns for naming and IP addresses which makes any targets more difficult to figure out. These methods are in effect 'digital hygiene' and attempt to provide at least some level of security with HTTP and TFTP. 

The Digital Rebar provisioning system does not include SSH keys in provisioning channels.

Do not deliver any confidential or identifying information via unsecured protocols. All credentials and configuration information should be routed through secured channels. Be aware that provisioning channels are not secure.

In cases where extreme security is required, provisioning channels can be secured with UEFI (Unified Extensible Firmware Interface). Therefore UEFI may be a good choice for those who are especially concerned with security.

Make sure the DHCP servers only use white-list or never automatically accept discovered servers and never trust discovered servers without some form of verification. One way to ensure discovery verification is to use a TPM. A TPM, or Trusted Platform Module, allows the user to sign an encryption key onto a server. Configuring a TPM as part of a boot process is one of the best security practices. Using a TPM requires a trusted system, as it cannot allow any node to just declare itself; the system needs a way to validate them. For more information, reference Chapter 2.4 "White-list vs Discovery."

One of the problems with configuration-based provisioning is that it requires access to the server in order to change the configuration, such as with Cobbler or Stacky. In those cases, people have to give sensitive access to a server to a broad range of people.

The API-driven configuration used by MaaS and RackN allows for easier access to a system, but that access is only for the API endpoint rather than the full server. API-driven configuration has the benefit of fewer people with root access to deep infrastructure, and it also gives the system administrator the ability to control who has access to the system and what they can do. It is critically important to carefully monitor who has access. 

In every case, who has access to a system is the most fundamental part of the infrastructure. Through the Digital Rebar API, new SSH keys can be injected by someone to give themselves access to the systems.
