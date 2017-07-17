



Cloud Init
==========

Cloud-init is the Ubuntu package that handles early initialization of a cloud instance. A cloud instance is a virtual server instance from a public or private loud network. 

In cloud instance computing, single hardware is implemented into software and run on top of multiple computers. If there is a need for more computers, it is simple to add more. Essentially, cloud-init allows for expansion into multiple servers and computers. A server on the cloud can be moved from physical machine to physical machine without being taken down. 

What cloud-init can do (courtesy of cloud-init docs):

	-setting a default locale
	-setting an instance hostname
	-generating instance SSH private keys
	-adding SSH keys to a user's .ssh/authorized_keys for log-in
	-setting up ephemeral mount points
	-configuring network devices

===========

cloud-init is cloud-based pattern for injecting config patterns into new system 

each server assigned init file w/ details for coming online. substitutes for preseed config. still need configuration. 

curtin (ubuntu tech) will read file and do post-config like preseed of kickstart. still need file unique to each server for each injection.

servers are p much same in cloud. 

popular in container linux (coreOS) or linuxkit or atomic where preseed-like isn't supported bc OS is immutable operating system

immutable OS: install image doesn't get configured. get image that shouldn't be changed. run the script and give that info. it is a repeatable way to do an install on servers. 

value of cloud-init: more comfortable for people doing cloud
	take cloud files, add extra hardware, and it still works for physical machines. 

goal is shared ownership between cloud and metal. developer owns app part, operator injects things needed for metal specific. cloud portability