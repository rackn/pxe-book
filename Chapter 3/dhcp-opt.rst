



DHCP Options:
=============

chapter 3.1 'Getting on the Network' explained the process of how a DHCP server provides a new machine with an IP address by sending it an IP address in a UDP packet. This section takes a closer look at the other information sent to the new machine in that UDP packet.  

The UDP packet sent to a new machine by the DHCP server is called a DHCPack.  Any DHCP options, also known as configuration parameters, requested in the machine's initial DHCPDiscover message are included along with the IP address in the DHCPack.  DHCP options are octet strings of variable lengths, where an octet is eight bits. The first four octets of the DHCP options field carry the "magic cookie" value, 99.139.83.99, to identify the message as a DHCP message and differentiate it from BOOTP messages.  The rest of the DHCP Option field contains the option code, length, and data of the DHCP option. The option code refers to a specific DHCP option and is one octet.  The length is the number of octets in the option (excluding those in the code and length subfields), and the option data is the data being sent.  

There are seven categories of DHCP option: RF C 1497 Vendor Extensions, IP Layer Parameters per Host, IP Layer Parameters per Interface, TCP Parameters, Application and Service Parameters, and DHCP Extensions. 

The following chart details the options in the last category, DHCP Extensions. 


=================================================================================================================================+
|Code Value|Octets|Name                        |Description                                                                      |
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| 50       | 4    | Requested IP Address       | DHCP client requests specific IP address                                        |
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| 51       | 4    | IP Address Lease Time      | DHCP client requests or DHCP server offers a lease duration, measured in seconds|
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| 52       | 1    | Option Overload            | Indicates that SName and/or File fields carry options rather than information   |
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| -        | -    | Option value: 1            | File field is carrying option data                                              |
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| -        | -    | Option value: 2            | SName field is carrying option data                                             |
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| -        | -    | Option value: 3            | Both fields are carrying option data                                            |
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| 53       | 1    | DHCP Message Type          | Indicates type of DHCP message                                                  |
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| -        | -    | Option value: 1            | DHCPDISCOVER                                                                    |
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| -        | -    | Option value: 2            | DHCPOFFER                                                                       |
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| -        | -    | Option value: 3            | DHCPREQUEST                                                                     |
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| -        | -    | Option value: 4            | DHCPDECLINE                                                                     |
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| -        | -    | Option value: 5            | DHCPACK                                                                         |
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| -        | -    | Option value: 6            | DHCPNAK                                                                         |
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| -        | -    | Option value: 7            | DHCPRELEASE                                                                     |
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| -        | -    | Option value: 8            | DHCPINFORM                                                                      | 
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| 54       | 4    | Server Identifier          | IP address of a DHCP server, which identifies DHCP server in messages it        |
|          |      |                            | sends and in messages from a client accepting a DHCP server's lease.            |
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| 55       | Var  | Parameter Request List     | DHCP client requests list of configuration parameter values from a DHCP server  |
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| 56       | Var  | Message                    | Indicates an error or other message                                             |
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| 57       | 2    | Maximum DHCP Message Size  | Indicates maximum size message client or server is willing to accept            |
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| 58       | 4    | Renewal (T1) Time Value    | DHCP server tells client what value to use for renewal timer                    |
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| 59       | 4    | Rebinding (T2) Time Value  | DHCP server tells client what value to use for rebinding timer                  |
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| 60       | Var  | Vendor Class Identifier    | DHCP clients specifies its vendor and configuration                             |
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| 61       | Var  | Client Identifier          | DHCP client indicates a unique client ID different from DHCP default;           |
|          |      |                            | used by DHCP server to index its configuration parameter database               |
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| 66       | Var  | TFTP Server Name           | Indicates to recipient that TFTP server name which would normally be in SName   |
|          |      |                            |  field when SName field is being used for options through option overload       |
+----------+------+----------------------------+---------------------------------------------------------------------------------+
| 67       | Var  | Bootfile Name              | Indicates to recipient that bootfile name that would normally be in File field  | 
|		   |	  |			                   | when File field is being used for options through option overload               |
=================================================================================================================================+