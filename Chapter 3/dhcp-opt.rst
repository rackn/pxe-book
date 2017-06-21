



DHCP Options
============

<i>Getting on the Network</i> covered how a DHCP server provides a new machine with an IP address by sending it in a UDP packet. This section will look further into the other information sent to the new machine in that UDP packet. 

The UDP packet sent to the new machine by the DHCP server is called a DHCPack. Any DHCP options, or configuration parameters,  requested in the machine's UDP packet are included along with the IP address in the DHCPack. DHCP options are octet strings of variable lengths, where an octet is eight bits. The first four octets of the DHCP option field carry the "magic cookie" value, 99.139.83.99 to identify the message as a DHCP message and differentiate it from BOOTP messages. The rest of the DHCP Option field contains the option code, length, and data of the DHCP option. The option code refers to a specific DHCP option and is one octet. The length is the number of octets in the option (excluding those in the code and length subfields), and the option data is the data being sent. 

There are seven categories of DHCP options: RFC 1497 Vendor Extensions, IP Layer Parameters per Host, IP Layer Parameters per Interface, TCP Parameters, Application and Service Parameters, and DHCP Extensions. The focus of this section is the last category, DHCP Extensions. 

The UDP packet sent from the new machine would include the desired DHCP options which are then fulfilled and sent back by the DHCP server in the DHCPack. 


<make a chart for all this info. 4 columns: code value, data length in octets, name, description>

50 - 4 - Requested IP Address: DHCP client requests specific IP address
51 - 4 - IP Address Lease Time: DHCP client requests specific lease duration or DHCP server offers specific lease duration. Measured in seconds
52 - 1 - Option Overload: Indicates to recipient of message that SName and/or File fields carry options rather than normal information 
		1 - File field is carrying option data
		2 - SName field is carrying option data
		3 - Both fields are carrying option data
53 - 1 - DHCP Message Type: Indicates type of DHCP message 
		1 - DHCPDISCOVER
		2 - DHCPOFFER
		3 - DHCPREQUEST
		4 - DHCPDECLINE
		5 - DHCPACK
		6 - DHCPNAK
		7 - DHCPRELEASE
		8 - DHCPINFORM
54 - 4 - Server Identifier: IP address of a DHCP server, which identifies DHCP server in messages it sends and in messages from a client accepting a DHCP server's lease. 
55 - variable - Parameter Request List: DHCP client requests list of configuration parameter values from a DHCP server
56 - variable - Message: Indicates an error or other message
57 - 2 - Maximum DHCP Message Size: Indicates maximum size message client or server is willing to accept
58 - 4 - Renewal (T1) Time Value: DHCP server tells client what value to use for renewal timer
59 - 4 - Rebinding (T2 Time Value: DHCP server tells client what value to use for rebinding timer
60 - variable -	Vendor Class Identifier: DHCP clients specifies its vendor and configuration
61 - variable -	Client Identifier: DHCP client indicates a unique client ID different from DHCP default; used by DHCP server to index its configuration parameter database
66 - variable - TFTP Server Name: Indicates to recipient that TFTP server name that would normally be in SName field when SName field is being used for options through option overload
67 - variable - Bootfile Name: Indicates to recipient that bootfile name that would normally be in File field when File field is being used for options through option overload
